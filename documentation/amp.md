# Como integrar a AdOpt com Google AMP

A coleta de consentimentos de cookies utilizando AMP pode ser um pouco complexa, porém a AdOpt está aqui para te ajudar. O AMP é muito conhecido por otimizar a navegação em páginas da internet por dispositivos móveis, ele permite a captura do consentimento do uso de cookies possibilitando o bloqueio de certos conteúdos com base na resposta do usuário.

## Inserindo a AdOpt no seu site AMP

### Passo 1 - Adicionando os Scripts necessários

O AMP exige a inserção dos Scripts no head da sua página HTML para que seja possível a utilização dos seus elementos customizados na página. Para isso, copie esses scripts e coloque-os no head de um arquivo HTML do seu site.

```html
<!DOCTYPE html>
<html>
    <head>
		...
       <script 
		  async 
		  custom-element="amp-script" 
		  src="https://cdn.ampproject.org/v0/amp-script-0.1.js"></script>
		<script
		  async
		  custom-element="amp-consent"
		  src="https://cdn.ampproject.org/v0/amp-consent-0.1.js"></script>
		...
    </head>
    <body>
		...
    </body>
</html>
```

### Passo 2 - Adicionando os estilos

Seguindo, adicione o seguinte style no head do seu documento:

```html
<!DOCTYPE html>
<html>
    <head>
		...
       <style amp-custom>
		         .card-primary{color:rgb(0,221,128)}.card-text{color:rgb(52,70,76)}.ao-ball-button{position:fixed;bottom:10px;left:15px;width:70px;height:70px;cursor:pointer;opacity:0.5;z-index:10000;border:none;outline:none;background:none;transition:500ms}.ao-ball-button:hover{opacity:1}.ao-ball-button-path{fill:rgb(0, 221, 128)}.ao-ball-button img{max-width:50px;max-height:50px;position:absolute;left:50%;top:50%;transform:translate(-50%,-50%)}.ao-Bar{width:100%;height:80px;box-sizing:border-box;padding:0px;position:fixed;bottom:0px;font-size:11px;line-height:1.5em;z-index:1000002;box-shadow:0 3px 6px 0 rgba(0, 0, 0, 0.2);user-select:none;background:var(--bgColor)}.ao-Bar a{font-weight:bold}.ao-bar-center{max-width:350px;width:calc(100vw - 40px);max-height:170px;height:calc(100vh - 100px);bottom:90px;margin-left:auto;margin-right:auto;left:0;right:0;border-radius:15px;position:fixed;flex-wrap:wrap;background:#fff}.ao-Inner{box-sizing:border-box;height:100%;width:100%;display:flex;align-items:center;padding:20px;justify-content:space-between}.ao-bar-center .ao-Inner{flex-wrap:wrap}.ao-ConsentText{box-sizing:border-box;min-width:100%;max-width:100%;text-align:left}.ao-bar-center .ao-ConsentText{min-width:100%;max-width:100%;min-height:0;max-height:100%;font-size:13px}.ao-ConsentText a{text-decoration:underline;font-size:13px}.ao-Preferences{font-weight:bold;text-transform:uppercase;text-decoration:none;padding:10px;border-radius:20px;cursor:pointer;font-size:11px;border-radius:20px;min-width:45%;outline:none;background:none;color:rgb(52, 70, 76);border:1px solid rgb(52,70,76);background-color:none}.ao-AcceptAll{font-weight:bold;text-transform:uppercase;padding:10px;border:none;border-radius:20px;cursor:pointer;font-size:11px;min-width:45%;outline:none;color:#fff;background-color:rgb(0, 221, 128);box-shadow:rgb(0, 221, 128) 0px 10px 28px -12px}.ao-flex{display:flex;justify-content:space-between;width:100%}.ao-bar-center .ao-flex{flex-wrap:no-wrap}.ao-bar-center .ao-flex button{max-width:49%;min-width:45%}.ao-Bar h3{font-size:13px;margin:0 0 10px;padding:0;line-height:1.25em}.ao-Bar span{line-height:2em;padding:0}.ao-ConsentText a{font-size:11px}.ao-ConsentText .adopt-logo{color:rgb(0, 221, 128);position:absolute;top:25px;right:25px;text-decoration:none;font-weight:400;width:60px;text-align:right;white-space:nowrap;font-size:13px}.adopt-logo span{top:-3px;position:relative;font-size:11px;text-decoration:none}
		</style>
		...
    </head>
    <body>
		...
    </body>
</html>
```

### Passo 3 - Adicionando o AMP-Consent

Finalmente, adicione o **amp-consent** ao **body** do seu documento. Esse é o elemento responsável pela captura do consentimento do usuário.


```html
<!DOCTYPE html>
<html>
    <head>
		...
    </head>
    <body>
		...
		<amp-consent id="adoptConsent" layout="nodisplay">
        <script type="application/json">
          {
            "consentInstanceId": "AdoptConsent",
            "consentRequired": true,
            "promptUI": "consent-ui",
            "postPromptUI": "reprompt-dialog"
          }
        </script>
        <button 
        id="reprompt-dialog" 
        class="ao-ball-button ao-button-left"
        on="tap:adoptConsent.prompt">
          <svg version="1.1" viewBox="0 0 330 330" style="width: auto; height: auto" id='logoAdoptReprompt' > <defs id="defs2"> <filter id="filter43" style="color-interpolation-filters: srgb"> <feGaussianBlur stdDeviation="5 3.8" result="blur" id="feGaussianBlur41" ></feGaussianBlur> </filter> <filter id="filter4609" x="-0.156" width="1.312" y="-0.156" height="1.312" style="color-interpolation-filters: srgb" > <feGaussianBlur stdDeviation="15.996187" id="feGaussianBlur4611" ></feGaussianBlur> </filter> </defs> <circle id="path53" cx="163.82628" cy="165.72458" r="138.43221" transform="matrix(0.92523923,0,0,0.92523923,7.146084,13.940543)" style=" fill: none; stroke: rgb(0, 0, 0); stroke-width: 17.9154; stroke-miterlimit: 4; stroke-dasharray: none; stroke-opacity: 0.5; filter: url('#filter4609'); " ></circle> <g id="g4680" transform="matrix(0.92523923,0,0,0.92523923,16.172283,23.815094)" > <g transform="translate(9.5495409,2.6750356)" id="g8"> <path id="path4" d="m 149.79668,4.8974491 c -75.969079,0 -137.548476,64.0910029 -137.548476,143.1799609 0,79.08897 61.579397,143.18009 137.548476,143.18009 75.96894,0 137.54846,-64.09112 137.54846,-143.18009 0,-79.088958 -61.57952,-143.1799609 -137.54846,-143.1799609 z M 231.90151,147.5504 160.81253,218.63938 a 38.015411,38.015411 0 0 1 -53.21188,0 L 67.681994,178.73376 A 37.203188,37.203188 0 0 1 120.2953,126.12058 l 13.91775,13.90151 45.08168,-45.081668 a 37.203224,37.203224 0 1 1 52.6133,52.613298 z" class='ao-ball-button-path' style="stroke-width: 3.25335" ></path> <path id="path6" d="m 224.37001,101.54799 a 27.715301,27.715301 0 0 0 -39.21273,0 l -44.72374,44.72054 -26.86951,26.8727 a 27.715301,27.715301 0 0 0 0,39.21273 l 0.92098,0.92099 a 27.715301,27.715301 0 0 0 39.21261,0 l 17.02486,-17.02486 54.56519,-54.56519 a 27.715301,27.715301 0 0 0 0,-39.21261 z m -90.16348,113.00514 a 21.914575,21.914575 0 1 1 21.90814,-21.92105 21.924336,21.924336 0 0 1 -21.90814,21.92105 z" class='ao-ball-button-path' style="stroke-width: 3.25335" ></path> </g> </g> </svg>
        </button>
        <div id="consent-ui">
          <button 
            id='dismissButton'
            on="tap:adoptConsent.dismiss"
            class="ao-ball-button ao-button-left">
              <svg version="1.1" viewBox="0 0 330 330" style="width: auto; height: auto" id='logoAdoptReprompt' > <defs id="defs2"> <filter id="filter43" style="color-interpolation-filters: srgb"> <feGaussianBlur stdDeviation="5 3.8" result="blur" id="feGaussianBlur41" ></feGaussianBlur> </filter> <filter id="filter4609" x="-0.156" width="1.312" y="-0.156" height="1.312" style="color-interpolation-filters: srgb" > <feGaussianBlur stdDeviation="15.996187" id="feGaussianBlur4611" ></feGaussianBlur> </filter> </defs> <circle id="path53" cx="163.82628" cy="165.72458" r="138.43221" transform="matrix(0.92523923,0,0,0.92523923,7.146084,13.940543)" style=" fill: none; stroke: rgb(0, 0, 0); stroke-width: 17.9154; stroke-miterlimit: 4; stroke-dasharray: none; stroke-opacity: 0.5; filter: url('#filter4609'); " ></circle> <g id="g4680" transform="matrix(0.92523923,0,0,0.92523923,16.172283,23.815094)" > <g transform="translate(9.5495409,2.6750356)" id="g8"> <path id="path4" d="m 149.79668,4.8974491 c -75.969079,0 -137.548476,64.0910029 -137.548476,143.1799609 0,79.08897 61.579397,143.18009 137.548476,143.18009 75.96894,0 137.54846,-64.09112 137.54846,-143.18009 0,-79.088958 -61.57952,-143.1799609 -137.54846,-143.1799609 z M 231.90151,147.5504 160.81253,218.63938 a 38.015411,38.015411 0 0 1 -53.21188,0 L 67.681994,178.73376 A 37.203188,37.203188 0 0 1 120.2953,126.12058 l 13.91775,13.90151 45.08168,-45.081668 a 37.203224,37.203224 0 1 1 52.6133,52.613298 z" class='ao-ball-button-path' style="stroke-width: 3.25335" ></path> <path id="path6" d="m 224.37001,101.54799 a 27.715301,27.715301 0 0 0 -39.21273,0 l -44.72374,44.72054 -26.86951,26.8727 a 27.715301,27.715301 0 0 0 0,39.21273 l 0.92098,0.92099 a 27.715301,27.715301 0 0 0 39.21261,0 l 17.02486,-17.02486 54.56519,-54.56519 a 27.715301,27.715301 0 0 0 0,-39.21261 z m -90.16348,113.00514 a 21.914575,21.914575 0 1 1 21.90814,-21.92105 21.924336,21.924336 0 0 1 -21.90814,21.92105 z" class='ao-ball-button-path' style="stroke-width: 3.25335" ></path> </g> </g> </svg>
            </button>
            <div
                id='disclaimerBar'
                class="ao-Bar ao-bar-center"
            >
                <div class="ao-Inner">
                <div class="ao-ConsentText">
                    <h3 class='card-primary'>
                    Controle sua privacidade
                    </h3>
                    <span
                    class='card-text'
                    ><span id='text'>Nosso site usa cookies para melhorar a navegação.</span> <br />
                    <a  id='privacyPolicy'
                        target="_blank"
                        class='card-primary'
						href='LINK_PARA_SUA_PÁGINA_DE_POLÍTICA_DE_PRIVACIDADE'
                        >Politica de privacidade</a>
                    -
                    <a  id='terms'
                        target="_blank"
                        class='card-primary'
						href='LINK_PARA_SUA_PÁGINA_DE_TERMOS_DE_USO'
                        >Termos de uso</a>
                    -
                    <a  id='optOut'
                        href="https://app.goadopt.io/7dbc9711-fe7a-4635-ab07-2d157a0bd11d/opt-out/ea121fef-5177-4cb1-97da-863a530d102b"
                        target="_blank"
                        class='card-primary'
                        >Opt-Out</a></span>
                    <br />
                    <a
                    href="https://goadopt.io/porque-aviso"
                    class="adopt-logo"
                    target="_blank"
                    style="color: rgb(0, 221, 128)"
                    >
                    <svg version="1.1" viewBox="0 0 330 330" style="width: 16px; height: 16px" > <defs id="defs2"> <filter id="filter43" style="color-interpolation-filters: srgb" > <feGaussianBlur stdDeviation="5 3.8" result="blur" id="feGaussianBlur41" ></feGaussianBlur> </filter> <filter id="filter4609" x="-0.156" width="1.312" y="-0.156" height="1.312" style="color-interpolation-filters: srgb" > <feGaussianBlur stdDeviation="15.996187" id="feGaussianBlur4611" ></feGaussianBlur> </filter> </defs> <circle id="path53" cx="163.82628" cy="165.72458" r="138.43221" transform="matrix(0.92523923,0,0,0.92523923,7.146084,13.940543)" style=" fill: none; stroke: rgb(0, 0, 0); stroke-width: 17.9154; stroke-miterlimit: 4; stroke-dasharray: none; stroke-opacity: 0.5; filter: url('#filter4609'); " ></circle> <g id="g4680" transform="matrix(0.92523923,0,0,0.92523923,16.172283,23.815094)" > <g transform="translate(9.5495409,2.6750356)" id="g8"> <path id="path4" d="m 149.79668,4.8974491 c -75.969079,0 -137.548476,64.0910029 -137.548476,143.1799609 0,79.08897 61.579397,143.18009 137.548476,143.18009 75.96894,0 137.54846,-64.09112 137.54846,-143.18009 0,-79.088958 -61.57952,-143.1799609 -137.54846,-143.1799609 z M 231.90151,147.5504 160.81253,218.63938 a 38.015411,38.015411 0 0 1 -53.21188,0 L 67.681994,178.73376 A 37.203188,37.203188 0 0 1 120.2953,126.12058 l 13.91775,13.90151 45.08168,-45.081668 a 37.203224,37.203224 0 1 1 52.6133,52.613298 z" style="fill: rgb(0, 221, 128); stroke-width: 3.25335" ></path> <path id="path6" d="m 224.37001,101.54799 a 27.715301,27.715301 0 0 0 -39.21273,0 l -44.72374,44.72054 -26.86951,26.8727 a 27.715301,27.715301 0 0 0 0,39.21273 l 0.92098,0.92099 a 27.715301,27.715301 0 0 0 39.21261,0 l 17.02486,-17.02486 54.56519,-54.56519 a 27.715301,27.715301 0 0 0 0,-39.21261 z m -90.16348,113.00514 a 21.914575,21.914575 0 1 1 21.90814,-21.92105 21.924336,21.924336 0 0 1 -21.90814,21.92105 z" style="fill: rgb(0, 221, 128); stroke-width: 3.25335" ></path> </g> </g> </svg>
                    <span>AdOpt</span></a
                    >
                    <br />
                </div>
                <div class="ao-flex">
                    <amp-script layout="container" script="buttons" style='width: 100%; justify-content: space-between; display: flex;'>
                      <button class="ao-Preferences" id="rejectButton" on="tap:adoptConsent.reject">Rejeitar</button>
                      <button class="ao-AcceptAll" id="acceptButton" on="tap:adoptConsent.accept">Aceitar</button>
                    </amp-script>
                    <script id="buttons" type="text/plain" target="amp-script">
                      let website_code = 'CÓDIGO_DO_SEU_WEBSITE';

					  const acceptButton=document.getElementById('acceptButton');const rejectButton=document.getElementById('rejectButton');const TAG_URI="https://api.goadopt.io/adopt/user";const EVENT_URI="https://api.goadopt.io/adopt/log/";let options={bundleVersion:1,cookieId:getCookie("AdoptId",website_code),website_code:website_code};let adoptCB;function sendOptIn(type="all"){const xhttp=new XMLHttpRequest();xhttp.onreadystatechange=(xhr)=>{if(xhr.target["readyState"]===4&&xhr.target["status"]===200){const optCookie={...options};setCookie("AdoptConsent",JSON.stringify(optCookie));} else{const optCookie={...options};delete optCookie['disclaimer'];setCookie("AdoptConsent",JSON.stringify(optCookie));}};const uri=TAG_URI;xhttp.open("POST",uri+`?website_code=${website_code}`,true);xhttp.withCredentials=true;xhttp.setRequestHeader("Content-Type","application/x-www-form-urlencoded");let form="";const consent={cookieId:getCookie("AdoptId",website_code),};form="value="+btoa(JSON.stringify(consent));xhttp.send(form);};function sendEvent(type="click"){const xhttp=new XMLHttpRequest();xhttp.open("POST",EVENT_URI+`?website_code=${website_code}`,true,);xhttp.withCredentials=true;xhttp.setRequestHeader("Content-Type","application/x-www-form-urlencoded");if(options){const event={type:type,bundleVersion:1,cookieId:getCookie("AdoptId",website_code),abTestGroup:options.abTestGroup,uri:encodeURIComponent(location.href),};xhttp.send("event="+JSON.stringify(event));}};function setCookie(cname,cvalue){localStorage.setItem(cname,cvalue);const d=new Date();d.setTime(d.getTime()+60*24*60*60*1000);const expires="expires="+d.toUTCString();if(cname=='AdoptConsent'){let optCookie=JSON.parse(cvalue);delete optCookie['cookie'];optCookie=JSON.stringify(optCookie);document.cookie=cname+"="+optCookie+";"+expires+";path=/";}else{document.cookie=cname+"="+cvalue+";"+expires+";path=/";}};function getCookie(cname,website_code=null){if(website_code==="preview"){return"preview";} if(localStorage.getItem(cname)){return localStorage.getItem(cname);} const name=cname+"=";const decodedCookie=decodeURIComponent(document.cookie);const ca=decodedCookie.split(";");for(let i=0;i<ca.length;i++){let c=ca[i];while(c.charAt(0)===" "){c=c.substring(1);} if(c.indexOf(name)===0){return c.substring(name.length,c.length);}} return"";};function removeCookie(name){document.cookie=name+"=;expires=Thu, 01 Jan 1970 00:00:01 GMT";} const uuidv4=()=>{return"xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx".replace(/[xy]/g,function(c){var r=(Math.random()*16)|0,v=c=="x"?r:(r&0x3)|0x8;return v.toString(16);});};function onLoad(){const url='https://auth.goadopt.io/amp/disclaimer-info/' const xhr=new XMLHttpRequest();xhr.responseType='json';xhr.open('POST',url);xhr.setRequestHeader('Content-Type','application/json');xhr.onload=function(){if(!getCookie("AdoptId",website_code)){setCookie("AdoptId",uuidv4());} options["account_id"]=JSON.parse(xhr.response.consentString)["account_id"];;};xhr.send(JSON.stringify({'consentInstanceId':website_code}));} onLoad();rejectButton.addEventListener('click',()=>{sendOptIn("all");sendEvent("amp-reject-all");});acceptButton.addEventListener('click',()=>{sendOptIn("all");sendEvent("amp-accept-all");});
                    </script>
                </div>
                </div>
            </div>
            </div>
        </div>
      </amp-consent>
    </body>
</html>
```

### Passo 4 - Direcionando seu usuário

Após adicionar o código do passo 3 ao seu projeto, insira a URL da sua página de termos de uso no lugar de "LINK_PARA_SUA_PÁGINA_DE_TERMOS_DE_USO" e a URL da sua página de políticas de privacidade no lugar de "LINK_PARA_SUA_PÁGINA_DE_POLÍTICA_DE_PRIVACIDADE" (basta localizar essas variáveis dentro do código e substituí-las).

Exemplo: 
```
	// <a  id='privacyPolicy'
	// 	  target="_blank"
	// 	  class='card-primary'
	// 	  href='LINK_PARA_SUA_PÁGINA_DE_POLÍTICA_DE_PRIVACIDADE'
	// 	  >Politica de privacidade</a>
	<a  id='privacyPolicy'
		target="_blank"
		class='card-primary'
		href='https://www.meu-site.com/politica-de-privacidade'
		>Politica de privacidade</a>
```


### Passo 5 - Adicionando o código do seu Website ao projeto

Você também deve adicionar o código do seu webSite. Para encontrar esse código, acesse sua conta no site da Adopt (link de acesso: "https://app.goadopt.io/"), clique em "código do aviso" (ele se encontra no canto superior do site).

Assim você terá acesso ao seu website_code:
```
website_code=19df3e78-7877-4f85-a905-5618169c40d1
```

Por fim, basta substituir "CÓDIGO_DO_SEU_WEBSITE" encontrado no código do item 3 por esse valor.

Exemplo:
```
// let website_code = 'CÓDIGO_DO_SEU_WEBSITE'; 
let website_code = '19df3e78-7877-4f85-a905-5618169c40d1';
```
