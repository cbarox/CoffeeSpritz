# CoffeeSpritz

CoffeeSpritz is a bookmarklet written in CoffeeScript that will let you read a selection of text using the speed reading technique popularized by [Spritz Incorporated](http://www.spritzinc.com/)

## Installation

To install CoffeeSpritz, create a bookmark entry with the location set to:

`javascript:(function(){var e;this.Spritz=function(){function t(){var t,n,r;this.rootDiv=document.createElement("div");this.rootDiv.id="spritz_root";this.rootDiv.align="center";this.rootDiv.style.position="fixed";this.rootDiv.style.zIndex="999";this.rootDiv.style.width="400px";this.rootDiv.style.left="50%";this.rootDiv.style.marginLeft="-200px";this.rootDiv.style.backgroundColor="white";this.rootDiv.style.borderColor="black";this.rootDiv.style.borderStyle="solid";this.resultDiv=document.createElement("div");this.resultDiv.id="spritz_result";this.rootDiv.appendChild(this.resultDiv);this.formerSpan=document.createElement("span");this.formerSpan.id="spritz_former";this.formerSpan.style.fontSize="32px";this.formerSpan.style.fontFamily="Droid Sans Mono";this.resultDiv.appendChild(this.formerSpan);this.pivotSpan=document.createElement("span");this.pivotSpan.id="spritz_pivot";this.pivotSpan.style.fontSize="32px";this.pivotSpan.style.fontFamily="Droid Sans Mono";this.pivotSpan.style.color="red";this.resultDiv.appendChild(this.pivotSpan);this.latterSpan=document.createElement("span");this.latterSpan.id="spritz_latter";this.latterSpan.style.fontSize="32px";this.latterSpan.style.fontFamily="Droid Sans Mono";this.resultDiv.appendChild(this.latterSpan);this.wpmSelectLabel=document.createElement("label");this.wpmSelectLabel.id="spritz_wpmlabel";this.wpmSelectLabel.innerHTML="WPM:";this.rootDiv.appendChild(this.wpmSelectLabel);this.wpmSelect=document.createElement("select");this.wpmSelect.id="spritz_wpm";for(t=r=200;r<=1e3;t=r+=50){n=document.createElement("option");n.text=t;this.wpmSelect.add(n)}this.rootDiv.appendChild(this.wpmSelect);this.startButton=document.createElement("button");this.startButton.id="spritz_start";this.startButton.onclick=function(){return e.go()};this.startButton.innerHTML="Start";this.rootDiv.appendChild(this.startButton);this.closeButton=document.createElement("button");this.closeButton.id="spritz_close";this.closeButton.onclick=function(){return e.hide()};this.closeButton.innerHTML="Close";this.rootDiv.appendChild(this.closeButton);this.running=false}t.prototype.getSelectionText=function(){var e,t,n,r,i,s;r="";if(window.getSelection){n=window.getSelection();if(n.rangeCount){e=document.createElement("div");for(t=i=0,s=n.rangeCount-1;0<=s?i<=s:i>=s;t=0<=s?++i:--i){e.appendChild(n.getRangeAt(t).cloneContents())}r=e.innerText||e.textContent}}else if(document.selection){if(document.selection.type==="Text"){r=document.selection.createRange().text}}if(r===""){return false}else{return r}};t.prototype.show=function(){if(document.body.firstChild){return document.body.insertBefore(this.rootDiv,document.body.firstChild)}else{return document.body.appendChild(this.rootDiv)}};t.prototype.hide=function(){return document.body.removeChild(this.rootDiv)};t.prototype.getWPM=function(){var e,t;e=this.wpmSelect.selectedIndex;t=this.wpmSelect.options[e].text;return parseInt(t)};t.prototype.setWord=function(e){var t,n,r,i;i=0;if(e.length>1){i=e.length/2-1}r=e.charAt(i);this.pivotSpan.innerHTML=r;n="";if(e.length>1){n=e.slice(i+1,e.length)}t="";if(e.length>2){t=e.slice(0,i)}if(t.length>n.length){while(t.length>n.length){n+=" "}}else if(n.length>t.length){while(n.length>t.length){t=" "+t}}this.formerSpan.innerHTML=t;return this.latterSpan.innerHTML=n};t.prototype.go=function(){var e,t,n,r,i,s;r=this.getSelectionText();if(!r||r.length===0){alert("Please select text to Spritz");return}this.running=true;i=r.split(/\s+/);t=0;e=function(e){return function(){if(t<i.length){return e.setWord(i[t++])}else{clearInterval(n);return e.running=false}}}(this);s=this.getWPM();return n=setInterval(e,6e4/s)};return t}();e=new Spritz;e.show();e.setWord("CoffeeSpritz")}).call(this)`

## Acknowledgements

The idea for this project and some algorithm ideas were taken from [OpenSpritz](https://github.com/Miserlou/OpenSpritz), definitely check them out if you like this project.

## Notice

CoffeeSpritz is not affiliated with [Spritz Incorporated](http://www.spritzinc.com/).
