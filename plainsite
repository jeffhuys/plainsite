#!/usr/bin/env node

const fs = require('fs')

const argv = process.argv
const command   = argv[2]

if (
  (command === 'embed' && argv.length < 5) ||
  (command === 'fetch' && argv.length < 4) ||
  (command !== 'embed' && command !== 'fetch')
) {
  console.log('Please provide a command (embed or fetch), a JPG image and (when embedding) a data file')
  console.log('Example: ./freeStorage embed img.jpg data.txt')
  console.log('         ./freeStorage fetch img.jpg')
  console.log(argv.length)
  process.exit(-1)
}

const imagePath = argv[3]

if      (command === 'embed') embed(imagePath, argv[4])
else if (command === 'fetch') console.log(fetch(imagePath))


function embed(imagePath, dataPath) {
  const image_raw = fs.readFileSync(imagePath).toString('binary')
  const data_raw  = fs.readFileSync(dataPath)

  const new_data = new Buffer(`${image_raw}__EDATA_START__${data_raw}__EDATA_END__`, 'binary')

  fs.writeFileSync(`${dataPath}_embedded_in_${imagePath}`, new_data)
}

function fetch(imagePath) {
  const regex = /__EDATA_START__([\s\S]*)__EDATA_END__/g
  const image_raw = fs.readFileSync(imagePath)

  const match = `${image_raw}`.match(regex)

  if (match && match.length !== 0) return match[0].replace('__EDATA_START__', '').replace('__EDATA_END__', '')

  return 'No data found'
}