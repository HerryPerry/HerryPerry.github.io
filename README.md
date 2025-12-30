
[index_Version5.html](https://github.com/user-attachments/files/24388481/index_Version5.html)
<!doctype html>
<html lang="it">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Stampa 3D - Ordina in PLA (Multi‑filamento)</title>
  <meta name="description" content="Ordina stampe 3D in PLA di alta qualità. Supporto multi-filamento: aggiungi più colori e note per ciascuno." />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg:#0f1113; --surface:#1a1c1f; --muted:#9aa3ad; --accent:#00d1ff; --white:#ffffff;
      --glass:rgba(255,255,255,0.03); --radius:12px; --maxwidth:1100px; --shadow:0 8px 30px rgba(2,6,23,0.6);
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0;font-family:"Inter",system-ui,-apple-system,"Segoe UI",Roboto,Arial;
      background:linear-gradient(180deg,var(--bg),#070808 120%); color:var(--white);
      -webkit-font-smoothing:antialiased; -moz-osx-font-smoothing:grayscale; line-height:1.45;
    }
    .container{max-width:var(--maxwidth);margin:0 auto;padding:32px 20px;}
    header{display:flex;justify-content:space-between;align-items:center;margin-bottom:18px}
    .brand{display:flex;gap:12px;align-items:center;text-decoration:none;color:var(--white)}
    .logo{width:44px;height:44px;border-radius:10px;background:linear-gradient(135deg,var(--surface),#111315);display:grid;place-items:center;box-shadow:var(--shadow)}
    nav{display:flex;gap:12px;align-items:center}
    nav a{color:var(--muted);text-decoration:none;padding:8px 12px;border-radius:8px;font-weight:600;font-size:14px}
    nav a:hover{color:var(--white);background:var(--glass)}
    .cta{background:linear-gradient(90deg,var(--accent),#00a7d6);color:#042027;padding:10px 16px;border-radius:10px;font-weight:700;text-decoration:none}
    .hero{display:grid;grid-template-columns:1fr 420px;gap:28px;padding:26px;border-radius:var(--radius);background:linear-gradient(180deg,rgba(255,255,255,0.02),transparent);box-shadow:var(--shadow)}
    .hero-left h1{margin:0 0 12px 0;font-size:clamp(28px,4.5vw,40px);color:var(--white)}
    .hero-left p{margin:0 0 18px 0;color:var(--muted)}
    .note-material{margin-top:12px;padding:10px 12px;background:rgba(255,255,255,0.02);border-radius:10px;display:inline-flex;gap:10px;align-items:center;color:var(--muted);font-size:14px}
    section{margin-top:24px;padding:20px;border-radius:var(--radius);background:linear-gradient(180deg,rgba(255,255,255,0.01),transparent);border:1px solid rgba(255,255,255,0.02)}
    .section-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:18px}
    .card{padding:14px;border-radius:12px;background:linear-gradient(180deg,rgba(255,255,255,0.01),transparent);border:1px solid rgba(255,255,255,0.02)}
    .colors-grid{display:flex;flex-wrap:wrap;gap:12px}
    .swatch{display:flex;gap:12px;align-items:center;padding:8px 10px;border-radius:10px;background:rgba(255,255,255,0.01);border:1px solid rgba(255,255,255,0.02)}
    .swatch .circle{width:40px;height:40px;border-radius:999px;border:2px solid rgba(255,255,255,0.04)}
    form{display:grid;gap:12px}
    .row{display:flex;gap:12px}
    .col{flex:1;display:flex;flex-direction:column;gap:8px}
    label{font-size:13px;color:var(--muted)}
    input[type="text"], input[type="email"], input[type="tel"], select, textarea{
      background:transparent;border:1px solid rgba(255,255,255,0.06);color:var(--white);padding:10px 12px;border-radius:10px;outline:none;font-size:15px
    }
    textarea{min-height:120px;resize:vertical}
    input:focus, select:focus, textarea:focus{border-color:rgba(0,209,255,0.18);box-shadow:0 8px 24px rgba(0,209,255,0.06)}
    .hint{font-size:13px;color:var(--muted)}
    .form-actions{display:flex;gap:10px;justify-content:flex-end;margin-top:6px}
    .btn-primary{background:var(--accent);color:#022428;padding:10px 16px;border-radius:10px;font-weight:700;border:none;cursor:pointer}
    .btn-ghost{background:transparent;border:1px solid rgba(255,255,255,0.06);color:var(--muted);padding:10px 14px;border-radius:10px;cursor:pointer}
    .error{color:#ff6b6b;font-size:13px;display:none}
    footer{margin-top:22px;color:var(--muted);font-size:13px;text-align:center}

    /* multi color UI */
    .colors-list{display:grid;gap:12px}
    .color-item{display:grid;grid-template-columns:1fr 40px;gap:8px;align-items:start}
    .color-controls{display:flex;gap:8px;align-items:center}
    .small-btn{background:rgba(255,255,255,0.03);border:1px solid rgba(255,255,255,0.04);color:var(--muted);padding:6px 8px;border-radius:8px;cursor:pointer}
    .remove-btn{background:#ff6b6b;color:#fff;border:none;padding:6px 8px;border-radius:8px;cursor:pointer}

    /* modal */
    .modal-backdrop{position:fixed;inset:0;background:rgba(2,6,23,0.6);display:none;place-items:center;z-index:60;padding:20px}
    .modal{background:linear-gradient(180deg, #0f1315, #0b0d0f);padding:18px;border-radius:12px;max-width:720px;width:100%;box-shadow:0 20px 60px rgba(2,6,23,0.7);border:1px solid rgba(255,255,255,0.03)}
    .summary{display:grid;gap:8px}
    .summary .line{display:flex;justify-content:space-between;gap:12px}
    .summary .label{color:var(--muted)}
    .summary .value{font-weight:700;color:var(--white)}

    /* honeypot (off-screen) */
    .hp{position:absolute;left:-9999px;top:auto;width:1px;height:1px;overflow:hidden}

    @media (max-width:1000px){.hero{grid-template-columns:1fr}.section-grid{grid-template-columns:1fr}.row{flex-direction:column}}
    @media (max-width:520px){.container{padding:14px};nav{display:none}}
  </style>
</head>
<body>
  <div class="container">
    <header>
      <a class="brand" href="#home">
        <div class="logo" aria-hidden="true">
          <svg width="26" height="26" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M3 16.5L12 21l9-4.5V6.5L12 2 3 6.5v10z" fill="url(#g)"/><defs><linearGradient id="g" x1="0" x2="1"><stop offset="0" stop-color="#00d1ff"/><stop offset="1" stop-color="#7CFF5A"/></linearGradient></defs></svg>
        </div>
        <div>
          <div style="font-weight:800;font-size:16px">Stampa 3D - PLA Pro</div>
          <div style="font-size:12px;color:var(--muted)">Ordini & Multi‑filamento</div>
        </div>
      </a>

      <nav aria-label="Navigazione">
        <a href="#vantaggi">Vantaggi</a>
        <a href="#colori">Colori</a>
        <a href="#contatto" class="cta">Ordina ora</a>
      </nav>
    </header>

    <main id="home">
      <section class="hero" aria-labelledby="hero-title">
        <div class="hero-left">
          <h1 id="hero-title">Ordina la tua stampa 3D in PLA — anche multi‑filamento</h1>
          <p>Ora puoi scegliere più colori/filamenti per lo stesso ordine: aggiungi nuove righe di colore e specifica per ciascuna come deve essere utilizzata.</p>
          <div style="display:flex;gap:12px">
            <a class="btn-primary" href="#contatto">Ordina ora</a>
            <a class="btn-ghost" href="#servizio">Come funziona</a>
          </div>
          <div class="note-material" style="margin-top:14px"><strong style="color:var(--white)">Materiale:</strong><span>PLA di alta qualità • <em style="color:var(--muted)">Altri materiali disponibili prossimamente</em></span></div>
        </div>

        <div class="card" style="max-width:420px">
          <h3 style="margin-top:0">Dettagli rapidi</h3>
          <p class="hint">Tempi tipici: 1–4 giorni lavorativi. Preventivo gratuito via email. Spedizioni principalmente in Italia.</p>
          <div style="margin-top:12px">
            <strong>Contatto email:</strong><br>
            <a href="mailto:sitotraker0@gmail.com" style="color:var(--accent);text-decoration:none">sitotraker0@gmail.com</a>
          </div>
        </div>
      </section>

      <section id="vantaggi" aria-labelledby="vantaggi-title">
        <h2 id="vantaggi-title">Perché PLA</h2>
        <div class="section-grid" style="margin-top:12px">
          <div class="card">
            <p class="hint">Il PLA è facile da stampare, con ottima finitura estetica e adatto per prototipi e oggetti decorativi.</p>
            <ul class="hint" style="margin-top:8px">
              <li>Facile da stampare</li>
              <li>Buona definizione dei dettagli</li>
              <li>Sostenibile (origina da risorse rinnovabili)</li>
            </ul>
          </div>
          <div class="card">
            <h4 style="margin:0">Uso consigliato</h4>
            <p class="hint" style="margin-top:8px">Prototipi, modelli architettonici, gadget e oggetti decorativi.</p>
          </div>
        </div>
      </section>

      <section id="colori" aria-labelledby="colori-title">
        <h2 id="colori-title">Galleria colori</h2>
        <div style="margin-top:12px" class="colors-grid">
          <div class="swatch"><div class="circle" style="background:#0f0f0f"></div><div class="label">Nero</div></div>
          <div class="swatch"><div class="circle" style="background:#ffffff;border:1px solid rgba(0,0,0,0.12)"></div><div class="label" style="color:#111">Bianco</div></div>
          <div class="swatch"><div class="circle" style="background:#9aa0a6"></div><div class="label">Grigio</div></div>
          <div class="swatch"><div class="circle" style="background:#d33c3c"></div><div class="label">Rosso</div></div>
          <div class="swatch"><div class="circle" style="background:#1766d1"></div><div class="label">Blu</div></div>
          <div class="swatch"><div class="circle" style="background:linear-gradient(135deg,#b58b2a,#f1c564)"></div><div class="label">Oro</div></div>
        </div>
      </section>

      <section id="servizio" aria-labelledby="servizio-title">
        <h2 id="servizio-title">Servizio su richiesta</h2>
        <div style="margin-top:10px" class="card">
          <p class="hint">Invia file STL/OBJ o link da Thingiverse/Printables. Specifica scala, riempimento e finiture. Se vuoi spedizioni internazionali, seleziona il paese: per paesi diversi dall'Italia la richiesta sarà valutata manualmente.</p>
        </div>
      </section>

      <section id="contatto" aria-labelledby="contatto-title">
        <h2 id="contatto-title">Modulo d'ordine</h2>
        <p class="hint">Compila il modulo per ricevere il preventivo via email. Se chiedi spedizione fuori Italia la richiesta sarà valutata manualmente e potresti ricevere costi aggiuntivi.</p>

        <form id="orderForm" action="https://formsubmit.co/sitotraker0@gmail.com" method="POST" target="_blank" novalidate>
          <!-- Honeypot anti-spam -->
          <input type="text" name="_honey" class="hp" tabindex="-1" autocomplete="off">

          <!-- Format the email as a table -->
          <input type="hidden" name="_template" value="table">
          <input type="hidden" name="_subject" value="Nuovo ordine - Stampa 3D">
          <input type="hidden" name="_captcha" value="false">
          <!-- Hidden field that will contain the serialized colors list -->
          <input type="hidden" id="hiddenColors" name="Colori">

          <div class="row">
            <div class="col">
              <label for="name">Nome completo</label>
              <input id="name" name="Nome" type="text" placeholder="Mario Rossi" required>
              <div class="error" id="err-name">Inserisci un nome.</div>
            </div>
            <div class="col">
              <label for="email">Email</label>
              <input id="email" name="Email" type="email" placeholder="tuo@esempio.com" required>
              <div class="error" id="err-email">Inserisci un'email valida.</div>
            </div>
          </div>

          <div class="row">
            <div class="col">
              <label for="phone">Telefono</label>
              <input id="phone" name="Telefono" type="tel" placeholder="+39 333 1234567" required>
              <div class="error" id="err-phone">Inserisci un numero di telefono.</div>
            </div>

            <div class="col">
              <label for="qty">Quantità (pezzi / multi‑pezzo)</label>
              <input id="qty" name="Quantità" type="text" placeholder="1" value="1" required>
            </div>
          </div>

          <!-- Multi-color section -->
          <div>
            <label>Colori / Filamenti (puoi aggiungere più righe)</label>
            <div style="margin-top:8px" class="hint">Per ogni colore specifica dove usarlo o altre istruzioni (es. "coperchio", "bordi", "parte interna").</div>

            <div class="colors-list" id="colorsList" style="margin-top:12px">
              <!-- template for color item generated by JS; one initial item inserted by script -->
            </div>

            <div style="margin-top:8px; display:flex; gap:8px; align-items:center">
              <button type="button" id="addColorBtn" class="small-btn">+ Aggiungi colore</button>
              <div class="hint" style="margin-left:6px">Aggiungi più filamenti se il modello richiede più colori.</div>
            </div>
            <div class="error" id="err-colors" style="display:none">Aggiungi almeno un colore.</div>
          </div>

          <hr style="border:none;height:1px;background:rgba(255,255,255,0.03);margin:14px 0">

          <div class="row">
            <div class="col">
              <label for="street">Indirizzo (Via / Nr.)</label>
              <input id="street" name="Via" type="text" placeholder="Via Roma 1" required>
              <div class="error" id="err-street">Inserisci l'indirizzo.</div>
            </div>
            <div class="col">
              <label for="city">Città</label>
              <input id="city" name="Città" type="text" placeholder="Milano" required>
              <div class="error" id="err-city">Inserisci la città.</div>
            </div>
          </div>

          <div class="row" style="align-items:flex-end">
            <div class="col">
              <label for="zip">CAP</label>
              <input id="zip" name="CAP" type="text" placeholder="20100" required>
              <div class="error" id="err-zip">Inserisci il CAP.</div>
            </div>

            <div class="col">
              <label for="country">Paese di destinazione</label>
              <select id="country" name="Paese" required>
                <option value="Italia" selected>Italia</option>
                <optgroup label="Unione Europea">
                  <option value="Austria">Austria</option>
                  <option value="Belgio">Belgio</option>
                  <option value="Bulgaria">Bulgaria</option>
                  <option value="Cipro">Cipro</option>
                  <option value="Croazia">Croazia</option>
                  <option value="Danimarca">Danimarca</option>
                  <option value="Estonia">Estonia</option>
                  <option value="Finlandia">Finlandia</option>
                  <option value="Francia">Francia</option>
                  <option value="Germania">Germania</option>
                  <option value="Grecia">Grecia</option>
                  <option value="Irlanda">Irlanda</option>
                  <option value="Lettonia">Lettonia</option>
                  <option value="Lituania">Lituania</option>
                  <option value="Lussemburgo">Lussemburgo</option>
                  <option value="Malta">Malta</option>
                  <option value="Paesi Bassi">Paesi Bassi</option>
                  <option value="Polonia">Polonia</option>
                  <option value="Portogallo">Portogallo</option>
                  <option value="Repubblica Ceca">Repubblica Ceca</option>
                  <option value="Romania">Romania</option>
                  <option value="Slovacchia">Slovacchia</option>
                  <option value="Slovenia">Slovenia</option>
                  <option value="Spagna">Spagna</option>
                  <option value="Svezia">Svezia</option>
                  <option value="Ungheria">Ungheria</option>
                </optgroup>
              </select>
              <div class="hint" id="shippingNote" style="display:none; margin-top:6px;">
                La spedizione fuori dall'Italia richiede approvazione manuale e può comportare costi aggiuntivi. Riceverai comunicazione via email.
              </div>
            </div>
          </div>

          <div>
            <label for="message">Descrizione / Link al modello (Thingiverse, Printables...)</label>
            <textarea id="message" name="Dettagli" placeholder="Inserisci link o descrizione del modello, scala, richieste particolari..." required></textarea>
            <div class="error" id="err-message">Aggiungi una descrizione o il link al modello.</div>
          </div>

          <div class="hint" style="margin-top:6px">Nota: non inserire numeri di carta o dati sensibili nel form. Ti invierò istruzioni sicure per il pagamento via email dopo la verifica dell'ordine.</div>

          <div class="form-actions">
            <button type="reset" class="btn-ghost">Pulisci</button>
            <button type="button" id="reviewBtn" class="btn-primary">Rivedi & Invia</button>
          </div>
        </form>
      </section>

      <footer>
        <div>© <strong>Stampa 3D - PLA Pro</strong> • Contatti: <a href="mailto:sitotraker0@gmail.com" style="color:var(--accent);text-decoration:none">sitotraker0@gmail.com</a></div>
        <div style="margin-top:6px" class="hint">Vendita principale: Italia. Spedizioni in altri paesi EU valutate manualmente.</div>
      </footer>
    </main>
  </div>

  <!-- Modal riepilogo -->
  <div id="modal" class="modal-backdrop" role="dialog" aria-modal="true" aria-hidden="true">
    <div class="modal" role="document" aria-labelledby="modalTitle">
      <h3 id="modalTitle">Riepilogo ordine</h3>
      <div class="summary" id="summary"></div>
      <p class="hint" style="margin-top:12px">Controlla i dati: dopo la conferma il modulo verrà inviato e riceverai il preventivo via email.</p>
      <div style="display:flex;gap:10px;justify-content:flex-end;margin-top:12px">
        <button id="cancelBtn" class="btn-ghost">Annulla</button>
        <button id="confirmBtn" class="btn-primary">Conferma e Invia</button>
      </div>
    </div>
  </div>

  <script>
    (function(){
      // Helper: create element from HTML
      function el(html){ const tmp = document.createElement('div'); tmp.innerHTML = html.trim(); return tmp.firstChild; }

      // Colors available
      const COLORS = [
        {v:'Nero', hex:'#0f0f0f'},
        {v:'Bianco', hex:'#ffffff'},
        {v:'Grigio', hex:'#9aa0a6'},
        {v:'Rosso', hex:'#d33c3c'},
        {v:'Blu', hex:'#1766d1'},
        {v:'Oro', hex:'linear-gradient(135deg,#b58b2a,#f1c564)'},
        {v:'Altro', hex:'#777777'}
      ];

      const colorsList = document.getElementById('colorsList');
      const addColorBtn = document.getElementById('addColorBtn');
      const errColors = document.getElementById('err-colors');

      // Template generator for a color item
      function createColorItem(index, data = {}) {
        const wrapper = document.createElement('div');
        wrapper.className = 'color-item card';
        wrapper.dataset.index = index;

        // build inner HTML
        wrapper.innerHTML = `
          <div style="display:grid;gap:8px">
            <div style="display:flex;gap:8px;align-items:center">
              <select name="color_select" class="color-select" required style="min-width:160px;">
                ${COLORS.map(c=>`<option value="${c.v}" ${data.color===c.v?'selected':''}>${c.v}</option>`).join('')}
              </select>
              <input type="text" name="color_part" class="color-part" placeholder="Dove usarlo? (es. coperchio, base...)" value="${data.part||''}" style="flex:1">
            </div>
            <textarea name="color_note" class="color-note" placeholder="Note aggiuntive per questo colore (es. % infill, layer orientation)">${data.note||''}</textarea>
          </div>
          <div class="color-controls">
            <button type="button" class="small-btn move-up" title="Sposta su" style="display:none">↑</button>
            <button type="button" class="small-btn move-down" title="Sposta giù" style="display:none">↓</button>
            <button type="button" class="remove-btn" title="Rimuovi colore">×</button>
          </div>
        `;

        // events
        const removeBtn = wrapper.querySelector('.remove-btn');
        removeBtn.addEventListener('click', ()=> {
          wrapper.remove();
          updateMoveButtons();
        });

        // move up/down (optional UX)
        const moveUp = wrapper.querySelector('.move-up');
        const moveDown = wrapper.querySelector('.move-down');
        moveUp.addEventListener('click', ()=>{
          const prev = wrapper.previousElementSibling;
          if(prev) colorsList.insertBefore(wrapper, prev);
          updateMoveButtons();
        });
        moveDown.addEventListener('click', ()=>{
          const next = wrapper.nextElementSibling;
          if(next) colorsList.insertBefore(next, wrapper);
          updateMoveButtons();
        });

        return wrapper;
      }

      // add initial color row
      function addColorRow(data){
        const idx = colorsList.children.length;
        const node = createColorItem(idx, data);
        colorsList.appendChild(node);
        updateMoveButtons();
      }

      // update visibility of move buttons
      function updateMoveButtons(){
        const items = Array.from(colorsList.children);
        items.forEach((it, i)=>{
          const up = it.querySelector('.move-up');
          const down = it.querySelector('.move-down');
          up.style.display = i === 0 ? 'none' : 'inline-flex';
          down.style.display = i === items.length -1 ? 'none' : 'inline-flex';
        });
      }

      addColorBtn.addEventListener('click', ()=> addColorRow());

      // initialize with one row
      addColorRow();

      // Country logic
      const countrySelect = document.getElementById('country');
      const shippingNote = document.getElementById('shippingNote');
      function checkCountryForApproval() {
        const country = countrySelect.value;
        shippingNote.style.display = country && country !== 'Italia' ? 'block' : 'none';
      }
      countrySelect.addEventListener('change', checkCountryForApproval);
      checkCountryForApproval();

      // Review & modal logic
      const form = document.getElementById('orderForm');
      const reviewBtn = document.getElementById('reviewBtn');
      const modal = document.getElementById('modal');
      const summary = document.getElementById('summary');
      const cancelBtn = document.getElementById('cancelBtn');
      const confirmBtn = document.getElementById('confirmBtn');
      const hiddenColors = document.getElementById('hiddenColors');

      function isEmailValid(v){ return /^[^\\s@]+@[^\\s@]+\\.[^\\s@]+$/.test(v); }
      function showError(id, show){ document.getElementById(id).style.display = show ? 'block' : 'none'; }

      function collectColors() {
        const items = Array.from(colorsList.children);
        const colors = items.map(it=>{
          const color = it.querySelector('.color-select').value;
          const part = it.querySelector('.color-part').value.trim();
          const note = it.querySelector('.color-note').value.trim();
          return { color, part, note };
        }).filter(c=>c.color); // filter valid
        return colors;
      }

      function validateAll(){
        let ok = true;
        const name = document.getElementById('name').value.trim();
        const email = document.getElementById('email').value.trim();
        const phone = document.getElementById('phone').value.trim();
        const street = document.getElementById('street').value.trim();
        const city = document.getElementById('city').value.trim();
        const zip = document.getElementById('zip').value.trim();
        const country = document.getElementById('country').value.trim();
        const message = document.getElementById('message').value.trim();
        const colors = collectColors();

        showError('err-name', !name); if(!name) ok=false;
        showError('err-email', !isEmailValid(email)); if(!isEmailValid(email)) ok=false;
        showError('err-phone', !phone); if(!phone) ok=false;
        showError('err-street', !street); if(!street) ok=false;
        showError('err-city', !city); if(!city) ok=false;
        showError('err-zip', !zip); if(!zip) ok=false;
        showError('err-message', !message); if(!message) ok=false;

        if(colors.length === 0) { errColors.style.display = 'block'; ok=false; } else { errColors.style.display = 'none'; }

        return ok;
      }

      function buildSummary(){
        summary.innerHTML = '';
        const fields = [
          ['Nome', document.getElementById('name').value.trim()],
          ['Email', document.getElementById('email').value.trim()],
          ['Telefono', document.getElementById('phone').value.trim()],
          ['Quantità', document.getElementById('qty').value.trim()],
          ['Paese', document.getElementById('country').value.trim()],
          ['Indirizzo', `${document.getElementById('street').value.trim()}, ${document.getElementById('city').value.trim()} (${document.getElementById('zip').value.trim()})`],
          ['Dettagli', document.getElementById('message').value.trim()]
        ];
        fields.forEach(([k,v])=>{
          const line = document.createElement('div'); line.className='line';
          const l = document.createElement('div'); l.className='label'; l.textContent = k;
          const val = document.createElement('div'); val.className='value'; val.textContent = v || '-';
          line.appendChild(l); line.appendChild(val); summary.appendChild(line);
        });

        // Colors list
        const colors = collectColors();
        const sectionTitle = document.createElement('div'); sectionTitle.className='label'; sectionTitle.style.marginTop='8px'; sectionTitle.textContent = 'Colori selezionati';
        summary.appendChild(sectionTitle);
        colors.forEach((c, i)=>{
          const div = document.createElement('div'); div.className='line';
          const l = document.createElement('div'); l.className='label'; l.textContent = `${i+1}. ${c.color}` + (c.part ? ` — ${c.part}` : '');
          const val = document.createElement('div'); val.className='value'; val.textContent = c.note || '-';
          div.appendChild(l); div.appendChild(val); summary.appendChild(div);
        });

        // prepare hiddenColors JSON (string)
        hiddenColors.value = JSON.stringify(colors);
      }

      reviewBtn.addEventListener('click', function(){
        if(!validateAll()) {
          const firstErr = document.querySelector('.error[style*="block"]');
          if(firstErr) firstErr.scrollIntoView({behavior:'smooth', block:'center'});
          return;
        }
        buildSummary();
        modal.style.display = 'grid';
        modal.setAttribute('aria-hidden','false');
        modal.scrollIntoView({behavior:'smooth'});
      });

      cancelBtn.addEventListener('click', function(){
        modal.style.display = 'none';
        modal.setAttribute('aria-hidden','true');
      });

      confirmBtn.addEventListener('click', function(){
        confirmBtn.disabled = true;
        confirmBtn.textContent = 'Invio...';
        // submit the form programmatically
        // hiddenColors already set by buildSummary
        form.submit();
        setTimeout(()=>{ confirmBtn.disabled=false; confirmBtn.textContent='Conferma e Invia'; modal.style.display='none'; modal.setAttribute('aria-hidden','true'); }, 800);
      });

      // keyboard accessibility
      document.addEventListener('keydown', function(e){
        if(e.key === 'Escape' && modal.style.display === 'grid'){ modal.style.display='none'; modal.setAttribute('aria-hidden','true'); }
      });

      // Reset behavior: clear colors and add a fresh one
      form.addEventListener('reset', function(){
        setTimeout(()=> {
          colorsList.innerHTML = '';
          addColorRow();
          checkCountryForApproval();
          errColors.style.display = 'none';
          document.querySelectorAll('.error').forEach(el=>el.style.display='none');
        }, 10);
      });

      // small helper to call existing checkCountryForApproval
      function checkCountryForApproval(){ 
        const country = countrySelect.value;
        shippingNote.style.display = country && country !== 'Italia' ? 'block' : 'none';
      }
      countrySelect.addEventListener('change', checkCountryForApproval);
    })();
  </script>
</body>
</html>
