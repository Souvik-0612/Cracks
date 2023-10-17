# Some cracks
## If some files required for permission to download in particlar pdfs you can just open the console and write the following code.
Actully this code making screenshots and add them up using basic **for loop**. Change the name of the file that you extracting, inside the function ```pdf.save```.
**Another thing to note that you have to load all the pages in the pdf. Why? Because I already said that this process is nothing but capturing the screenshots and add them up making a pdf so you have to load all the pages for successfully making a good pdf.**
Thanks.
```js
let jspdf = document.createElement( "script" );
jspdf.onload = function () {
let pdf = new jsPDF();
let elements = document.getElementsByTagName( "img" );
for ( let i in elements) {
let img = elements[i];
if (!/^blob:/.test(img.src)) {
continue ;
}
let canvasElement = document.createElement( 'canvas' );
let con = canvasElement.getContext( "2d" );
canvasElement.width = img.width;
canvasElement.height = img.height;
con.drawImage(img, 0, 0,img.width, img.height);
let imgData = canvasElement.toDataURL( "image/jpeg" , 1.0);
pdf.addImage(imgData, 'JPEG', 0, 0, 210, 297); // A4 size: 210mmx297mm
pdf.addPage();
}
pdf.save( "All You Need to know About Play.pdf" );
};
jspdf.src = 'https://cdnjs.cloudflare.com/ajax/libs/jspdf/1.3.2/jspdf.min.js' ;
document.body.appendChild(jspdf);
```
