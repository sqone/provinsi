# provinsi
Database provinsi seluruh indonesia

Penggunaan

Memanggil daftar provinsi

# default dopdown select
$('#desa').html('<option value="">Pilih Desa</option>');
$('#kecamatan').html('<option value="">Pilih Kecamatan</option>');
$('#kota').html('<option value="">Pilih Kota</option>');

# provinsi
var out_prov = '<option value="">Pilih Provinsi</option>';
$.getJSON('http://www.example.com/json/provinsi.json', function(response) {
  $.each(response, function(i, e) {
    out_prov += '<option value="'+e.id+'">'+e.name+'</option>';
  });
}).done(function() {
  $('#provinsi').html(out_prov);
});
// <select id="provinsi">Pilih Provinsi</select>

# kota
$('#provinsi').on('change', function() {
  var out_kota = '<option value="">Pilih Kota</option>';
  $.getJSON('http://www.example.com/json/kota/'+$(this).val()+'.json', function(response) {
    $.each(response, function(i, e) {
      out_kota += '<option value="'+e.id+'">'+e.name+'</option>';
    });
  }).done(function() {
    $('#kota').html(out_kota);
  });
});
// <select id="kota">Pilih Kota</select>

# kecamatan
$('#kota').on('change', function() {
  var out_kecamatan = '<option value="">Pilih Kecamatan</option>';
  $.getJSON('http://www.example.com/json/kecamatan/'+$(this).val()+'.json', function(response) {
    $.each(response, function(i, e) {
      out_kecamatan += '<option value="'+e.id+'">'+e.name+'</option>';
    });
  }).done(function() {
    $('#kecamatan').html(out_kecamatan);
  });
});
// <select id="kecamatan">Pilih Kecamatan</select>

# desa
$('#kecamatan').on('change', function() {
  var out_desa = '<option value="">Pilih Desa</option>';
  $.getJSON('http://www.example.com/json/desa/'+$(this).val()+'.json', function(response) {
    $.each(response, function(i, e) {
      out_desa += '<option value="'+e.id+'">'+e.name+'</option>';
    });
  }).done(function() {
    $('#desa').html(out_desa);
  });
});
// <select id="desa">Pilih Desa</select>
