# Dependencies
fs = require 'fs'
less = require 'less'
{exec} = require 'child_process'
util = require 'util'

# Build Variables
DATE = (new Date()).toUTCString()
LESSC = "./node_modules/.bin/lessc"
RAWR = './rawr.css'
RAWR_MIN = './rawr.min.css'
RAWR_SRC = './lib/rawr.less'
VERSION = "0.0.1"

HEADER_COMMENT = """
                 /**
                  * Rawwr! v#{VERSION}
                  *
                  * Copyright 2011 Ian Jennings
                  * Date: #{DATE}
                  */

                  """

# Tasks
task 'build', 'compile the less stylesheets', ->
  # Create the necessary streams
  tempFile = fs.createWriteStream("#{RAWR_SRC}.tmp")
  rawrFile = fs.createReadStream("#{RAWR_SRC}")

  # Write the header comment and the less to the temp file
  tempFile.write(HEADER_COMMENT)

  tempFile.on 'error', (err) ->
    return cleanUp(err)

  tempFile.once 'drain', (err) ->
    return cleanUp(err) if err
    util.pump rawrFile, tempFile, (err) ->
      return cleanUp(err) if err
      compileTempFile()

# Private Methods
compileTempFile = () ->
  util.print "Compiling..\n"
  exec "#{LESSC} #{RAWR_SRC}.tmp > #{RAWR}", (err) ->
    return cleanUp(err) if err
    exec "#{LESSC} #{RAWR_SRC}.tmp > #{RAWR_MIN} --compress", (err) ->
      cleanUp(err)

cleanUp = (err) ->
  fs.unlinkSync "#{RAWR_SRC}.tmp"
  throw err if err
  util.log "Rawr! It looks like you're good to go!\n"
