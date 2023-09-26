# eFaturaXSLT
XSLT şablonu eFatura ve eArşiv için tasarlanmıştır. Basitleştirilmiş stillerle, şirket imzası ve logosu ekleyebilme özelliği. Ayrıca yazıyla toplam tutar da var.

## Bu şablon aşağıdaki entegratörlerde test edilmiştir:
- DigitalPlanet
- Turmob
- QNB
- Logo
- Izibiz
- Uyumsoft

## Şablon Hakkında:
- **QR Kodu**: Şablona gömülü
- **Şirket Logosu**: Var
- **Şirket İmzası**: Var
- **Dış Görünüm**: CSS stili aracılığıyla değiştirilebilir
- **Yazıyla Toplam Tutar**: Şablona gömülü kod
- **Tek Şablon**: eFatura ve eArşiv için

### Ek Bilgi
Şablon önemli ölçüde basitleştirilmiş, normal bir stile getirilmiş, tamamen geçerli bir XSLT'dir. Tüm stiller kaldırılmış ve stil başlığına taşınmıştır.
Şablonda 3 alana görsel ekleyebilirsiniz:
.CompanyLogo
.Sign
.GIBLogo

Boş görsel eklemek için aşağıdaki formatı kullanabilirsiniz:
.Sign {
    content: url("data:image/gif;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs=");
    width: 120px;
    height: 120px;
}

İçerikte görselinizi base64 formatında doldurmanız gerekiyor.
data:image/gif;base64,R0lGODlhAQABAAD/ACwAAAAAAQABAAACADs= - bu satır, örneğin, sadece boş pikseller içermektedir.

İstediğiniz görseli base64 formatına çevirmek için aşağıdaki siteyi kullanabilirsiniz:
https://base64.guru/converter/encode/image
Sadece URL belirtiniz ya da  lokal bir dosyadan yükleyiniz, Output Format için de türü 'URI' seçiniz ve görselinizi base64 formatında elde edersiniz:

![image](https://github.com/IRPTeam/eFaturaXSLT/assets/68659714/6bc40e67-4ec9-4680-a61b-416896f22d5d)

Banka bilgileri ya da herhangi bir ek bilgiyi XML (UBL) dosyanızdaki Not alanına ekleyebilirsiniz. Mevcut şablon bunu en alta ekleyecektir.
Bunun için id='add_additional_text' içeren tabloyu bulabilirsiniz ve şu etiketi göreceksiniz:
<tr>
  <td>
	<div id="numberInputToWord"/>
  </td>
</tr>
    
Bunu kopyalayıp değiştirebilirsiniz:
<tr>
  <td>
	Some my important text
        <br/>
        New line of important test.
  </td>
</tr>

Sonucu şu siteden kontrol edebilirsiniz: https://xsltfiddle.liberty-development.net/.
XML'inizi sol alana ve XSLT'nizi sağ alana yerleştirin ve sonucu kontrol ediniz:
![image](https://github.com/IRPTeam/eFaturaXSLT/assets/68659714/a63d1866-f5a2-41a8-b019-2c21a82271b4)

Ancak mevcut hizmet komut dosyalarını yürütmediğinden "Number to Word" alanı boş olacaktır. Bunu görmek için sonucu bir *.html dosyası olarak kaydedin ve tarayıcınızda açın.

![image](preview.jpg)
