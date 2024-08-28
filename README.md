// ==UserScript==
// @name Vfs Portugal-01
// @namespace http://tampermonkey.net/
// @version 0.6
// @description try to take over VFS!
// @author Guedes
// @match https://row1.vfsglobal.com/*
// ==/UserScript==

var Email, Pwd, NumPass, DateN, ExpPass, Prenom, Nom, Genre, Phone, Interval, Visa, Ref, Country, CounTxt, MsgTxt, Txt, Gender,VisaNum,VisaPlace,VisaDur;
var Dora = 1;

Country = 0;
Email = "manueldiniz54@gmail.com"; // Email
Pwd = "Graciane2020#"; // mot de passe vfs
Phone = "923444395"; // numero tÃ©️lÃ©️phone
Gender = ["", 'Male', 'Female']; // 1 masculin, 2 Feminin
var VisaType = null;
var RefNum = "";



var Profiles = ["MIGUEL", "YOLANDA", "MARIA"];

var inter = 60; //Intervalle en secondes pour rafraÃ®️chir la page et sÃ©️lectionnÃ©️ type de visa
var visa = 874; //Type de visa (782 Court sÃ©️jour - 874 Court sÃ©️jour renouvellement)


/*---------Passeporte 01----------*/

function setForm() {
    if (Dora== 1) {
        //Profile 1
        NumPass = "N3215395";
        DateN = "25/05/2001";
        ExpPass = "04/03/2034";
        Prenom = "MIGUEL";
        Nom = "LUTETE";
        Genre = "1";

        //Renouvellement
        VisaNum = "";
        VisaPlace = "";
        VisaDur = "";
    }
    /*---------Passeporte 02----------*/
    else if (Dora == 2) {
        //Profile 2
        NumPass = "N3282799";
        DateN = "16/04/2001";
        ExpPass = "22/05/2034";
        Prenom = "YOLANDA";
        Nom = "MENDES";        Genre = 2;

        //Renouvellement
        VisaNum = "";
        VisaPlace = "";
        VisaDur = "";
    }
    /*----------Passeporte 03----------*/
    else if (Dora == 3) {
        //Profile 3
       NumPass = "";
        DateN = "";
        ExpPass = "";
        Prenom = "";
        Nom = "";
        Genre = 2;

        //Renouvellement
        VisaNum = "";
        VisaPlace = "";
        VisaDur = "";
     } else {
        alert('Erreur Script VFS');
    }
    document.title = Prenom + ' ' + Nom;
}

/*---------------------------------------------------------------------------------------------------------------------------------------------------------------------------*/

(function() {
    'use strict';
    $('.leftNav-ul').append('<li class="inactive-link"><a href="/Global-Appointment/Calendar/FinalCalendar">under configuration to Calendrie</a>');
    // Your code here...
})();

function addButton(i, index) {
    $('#sidebar').append('<button type="button" style="width: 100%; height: 50px;background-color:#03b131;border:0;font-size: 1.4em;margin-bottom: 10px;color:#fff;" id="Pro' + (index + 1) + '">' + i + '</button>');
}
$('#sidebar').append('<hr>');
Profiles.forEach(addButton);

$('#sidebar').on('click','#Pro1',function(){
    Dora = 1;
    setForm();
    fillForm();
})
$('#sidebar').on('click','#Pro2',function(){
    Dora = 2;
    setForm();
    fillForm();
})
$('#sidebar').on('click','#Pro3',function(){
    Dora = 3;
    setForm();
    fillForm();
})

function shiftDesign() {
  $('body').prepend('<h5 id="Alert" style="color: red; text-align: center; text-transforme: uppercase,background-color: teal;">Aucune Notfication</h5>');
  $('#header-title').css('margin', '2px');
  $('.header').height('40px');
  $('.logo').hide();
  $('.MsoNormal').hide();
}

function fillForm() {
  $("#PassportNumber").val(NumPass);
  $("#FirstName").val(Prenom);
  $("#LastName").val(Nom);
  $("#DateOfBirth").val(DateN);
  $("#PassportExpiryDate").val(ExpPass);
  $("#NationalityId option:contains('ANGOLA')").attr('selected', 'selected');
  $("#GenderId option:contains('" + Gender[Genre] + "')").attr('selected', 'selected');
  if ($('#VisaNumber').length) {
    $('#VisaNumber').val(VisaNum);
  }
  if ($('#PlaceOfIssuance').length) {
    $('#PlaceOfIssuance').val(VisaPlace);
  }
  if ($('#Duartion').length) {
    $('#Duartion').val(VisaDur);
  }
  if ($('#Mobile').length) {
    $('#Mobile').val(Phone);
  }
  if ($('#txtPassport').length) {
      $("#AURN").val(RefNum);
      $("#txtPassport").val(NumPass);
      $("#PrimaryEmailId").val(Email);
  }
   //$('#submitbuttonId').click();
}
(function() {
  document.title = Prenom + ' ' + Nom;
  if ($('#EmailId').length && $('#Password').length) {
      $('#EmailId').val(Email);
      $('#Password').val(Pwd);
  }
  var refresh = setInterval(function(){$('#VisaCategoryId').val(visa).change();}, inter*1000);

if($('#lblDate').text()!=''){
    clearInterval(refresh);
    var MsgTxt = new SpeechSynthesisUtterance('Rdv France disponible');
    window.speechSynthesis.speak(MsgTxt);
    $('#btnContinue').click();
}
})();
