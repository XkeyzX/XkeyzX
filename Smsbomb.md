const rl = require('readline-sync');
const colors = require('colors');
const title = require('./modules/title.js');
const fastBomber = require('./modules/sms.js');

title('Hosgeldiniz');

let telefon = rl.question('Telefon Numarasi Giriniz +90: '.green);
if (telefon.length != 10) {
  console.log('Telefon Numarası 10 Hanelı Olmalıdır. Örnek: 5401234521'.red);
  process.exit(1);
}
title('Numara: ' + telefon);

let miktar = rl.question("Kaç Tane SMS göndermek istiyorsun?: ".green);
if (isNaN(miktar)) return console.log('Lutfen Bir Rakam Giriniz'.red) && process.exit(1);
if (miktar.length == 0) {
  console.log('Miktar Giriniz:'.red);
  process.exit(1);
}
title(`Telefon: ${telefon} - Miktar: ${miktar}`);

console.log('SMS Gonderiliyor...'.rainbow);

fastBomber(telefon, miktar);
