# CoffeeSpritz

CoffeeSpritz is a bookmarklet written in CoffeeScript that will let you read a selection of text using the speed reading technique popularized by [Spritz Incorporated](http://www.spritzinc.com/)

CoffeeSpritz does not use any external libraries and does not make any AJAX calls

## Installation

To install CoffeeSpritz, create a bookmark entry with the URL set to:

`javascript:(function(){var e;this.Spritz=function(){function t(){var t,n,r,i;this.rootDiv=document.createElement("div");this.rootDiv.id="spritz_root";this.rootDiv.align="center";this.rootDiv.style.position="fixed";this.rootDiv.style.zIndex="9999";this.rootDiv.style.width="400px";this.rootDiv.style.left="50%";this.rootDiv.style.margin="0px";this.rootDiv.style.marginLeft="-200px";this.rootDiv.style.padding="10px";this.rootDiv.style.backgroundColor="white";this.rootDiv.style.borderColor="black";this.rootDiv.style.borderStyle="solid";this.rootDiv.style.borderWidth="3px";this.rootDiv.style.cursor="move";this.mouseDown=false;this.rootDiv.onmousedown=function(e){return function(){return e.mouseDown=true}}(this);this.rootDiv.onmouseup=function(e){return function(){return e.mouseDown=false}}(this);this.rootDiv.onmousemove=function(e){return function(t){if(e.mouseDown){e.rootDiv.style.left=t.clientX+"px";e.rootDiv.style.top=t.clientY-40+"px"}return t.preventDefault()}}(this);this.rootDiv.addEventListener("mouseleave",function(e){return function(){return e.mouseDown=false}}(this));t="bold 32px Courier";this.wordDiv=this.addUiElement("div","spritz_word",this.rootDiv);this.formerSpan=this.addUiElement("span","spritz_former",this.wordDiv);this.formerSpan.style.font=t;this.pivotSpan=this.addUiElement("span","spritz_pivot",this.wordDiv);this.pivotSpan.style.font=t;this.pivotSpan.style.color="red";this.latterSpan=this.addUiElement("span","spritz_latter",this.wordDiv);this.latterSpan.style.font=t;this.controlsDiv=this.addUiElement("div","spritz_controls",this.rootDiv);this.wpmSelectLabel=this.addUiElement("label","spritz_wpmlabel",this.controlsDiv);this.wpmSelectLabel.innerHTML="WPM:";this.wpmSelectLabel.removeAttribute("style");this.wpmSelect=this.addUiElement("select","spritz_wpm",this.controlsDiv);this.wpmSelect.onclick=function(e){return function(e){e.preventDefault();if(e.stopPropagation){return e.stopPropagation()}else{return e.cancelBubble=true}}}(this);for(n=i=200;i<=1e3;n=i+=50){r=document.createElement("option");r.text=n;this.wpmSelect.add(r)}this.wpmSelect.removeAttribute("style");this.startButton=this.addUiElement("button","spritz_start",this.controlsDiv);this.startButton.onclick=function(t){e.start();if(t.stopPropagation){return t.stopPropagation()}else{return t.cancelBubble=true}};this.startButton.innerHTML="Start";this.startButton.removeAttribute("style");this.closeButton=this.addUiElement("button","spritz_close",this.controlsDiv);this.closeButton.onclick=function(){return e.remove()};this.closeButton.innerHTML="Close";this.closeButton.removeAttribute("style");if(document.body.firstChild){document.body.insertBefore(this.rootDiv,document.body.firstChild)}else{document.body.appendChild(this.rootDiv)}}t.prototype.getSelectedText=function(){var e,t,n,r,i,s;r="";if(window.getSelection){n=window.getSelection();if(n.rangeCount){e=document.createElement("div");for(t=i=0,s=n.rangeCount-1;0<=s?i<=s:i>=s;t=0<=s?++i:--i){e.appendChild(n.getRangeAt(t).cloneContents())}r=e.innerText||e.textContent}}else if(document.selection){if(document.selection.type==="Text"){r=document.selection.createRange().text}}if(r===""){return false}else{return r}};t.prototype.addUiElement=function(e,t,n){var r;r=document.createElement(e);r.id=t;n.appendChild(r);return r};t.prototype.remove=function(){return document.body.removeChild(this.rootDiv)};t.prototype.getWPM=function(){var e,t;e=this.wpmSelect.selectedIndex;t=this.wpmSelect.options[e].text;return parseInt(t)};t.prototype.setWord=function(e){var t,n,r,i;i=0;if(e.length>1){i=e.length/2}r=e.charAt(i);this.pivotSpan.innerHTML=r;n="";if(e.length>2){n=e.slice(i+1,e.length)}t="";if(e.length>1){t=e.slice(0,i)}while(t.length>n.length){n+=" "}while(n.length>t.length){t=" "+t}this.formerSpan.innerHTML=t;return this.latterSpan.innerHTML=n};t.prototype.start=function(){var e,t,n,r,i,s;r=this.getSelectedText();if(!r||r.length===0){alert("Please select text to Spritz");return}r.replace(/\./,". ");i=r.split(/\s+/);t=0;e=function(e){return function(){if(t<i.length){return e.setWord(i[t++])}else{return clearInterval(n)}}}(this);s=this.getWPM();return n=setInterval(e,6e4/s)};return t}();e=new Spritz;e.setWord("CoffeeSpritz")}).call(this)`

In Google Chrome, you can add a bookmark by pushing Ctrl+Shift+B to reveal the bookmark bar, then right click the bar and select add page. Set the name of the bookmark to whatever you like and set the URL to the javascript above. Be sure to include the `javascript:` part in the url. For more info on the bookmark bar in Chrome, look [here](https://support.google.com/chrome/answer/95745?hl=en)

## How to use

To run CoffeeSpritz, simply open the bookmark that you created in the installation steps above, select the text you want to read, and click start.

If the CoffeeSpritz box gets in the way, you can grab it and drag it wherever you want on the page.

You can change the reading speed by changing the WPM (Words Per Minute). The average adult reading rate is 250 words per minute according to [Wikipedia](http://en.wikipedia.org/wiki/Speed_reading#Commercial_speed_reading_programs)

## Acknowledgements

The idea for this project and some algorithm ideas were taken from [OpenSpritz](https://github.com/Miserlou/OpenSpritz), definitely check them out if you like this project.

## Notice

CoffeeSpritz is not affiliated with [Spritz Incorporated](http://www.spritzinc.com/).
