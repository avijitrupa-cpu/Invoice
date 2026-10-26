# Invoice
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>All-in-One Invoice Generator</title>
<style>
:root{--blue:#155eef;--navy:#101d35;--bg:#f4f7fc;--line:#dce5f2;--muted:#64748b;--green:#0caa62;--red:#e5484d}
*{box-sizing:border-box}body{margin:0;font-family:Inter,system-ui,-apple-system,Segoe UI,Arial,sans-serif;background:var(--bg);color:#17233d}
.top{background:linear-gradient(110deg,#1258db,#0787e8);color:#fff;padding:17px 24px;display:flex;align-items:center;justify-content:space-between;gap:12px}.brand{font-size:22px;font-weight:800}.brand small{display:block;font-size:12px;font-weight:500;opacity:.85;margin-top:3px}
.app{display:grid;grid-template-columns:210px 1fr;min-height:calc(100vh - 68px)}aside{background:var(--navy);padding:18px 12px;color:#fff}aside a{display:block;color:#dce7fa;text-decoration:none;padding:12px;border-radius:8px;margin:4px 0;font-size:14px}aside a.active,aside a:hover{background:#155eef;color:white}.main{padding:22px;min-width:0}.welcome{display:flex;justify-content:space-between;align-items:center;gap:12px;margin-bottom:18px}.welcome h1{font-size:23px;margin:0 0 5px}.muted{color:var(--muted);font-size:13px}
.stats{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:12px;margin-bottom:18px}.stat,.panel{background:#fff;border:1px solid var(--line);border-radius:12px;box-shadow:0 2px 8px #0b23400a}.stat{padding:16px}.stat span{color:var(--muted);font-size:13px}.stat strong{display:block;font-size:24px;margin-top:9px}.layout{display:grid;grid-template-columns:minmax(0,1.12fr) minmax(320px,.88fr);gap:16px;align-items:start}.panel{padding:17px;margin-bottom:16px}.panel h2{font-size:17px;margin:0 0 16px;display:flex;align-items:center;justify-content:space-between;gap:10px}.section{font-size:13px;font-weight:800;color:#155eef;margin:18px 0 10px;border-bottom:1px solid #e8eef7;padding-bottom:7px}.formgrid{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:11px}.field{display:flex;flex-direction:column;gap:5px;min-width:0}.field.full{grid-column:1/-1}label{font-size:12px;color:#43516b;font-weight:650}input,textarea,select{width:100%;border:1px solid #cfdaea;border-radius:7px;padding:10px;font:inherit;font-size:13px;background:#fff;color:#17233d;min-width:0}textarea{resize:vertical;min-height:68px}input:focus,textarea:focus,select:focus{outline:2px solid #c7d9ff;border-color:#155eef}.btn{border:0;border-radius:8px;padding:10px 13px;font-weight:750;cursor:pointer;font-size:13px;display:inline-flex;align-items:center;justify-content:center;gap:7px}.primary{background:var(--blue);color:#fff}.green{background:var(--green);color:#fff}.light{background:#edf3ff;color:#1748a5;border:1px solid #d8e4ff}.danger{background:#fff0f0;color:#b4232c}.actions{display:flex;flex-wrap:wrap;gap:8px;margin-top:15px}.items-wrap{overflow:auto}table{width:100%;border-collapse:collapse;font-size:12px;min-width:560px}th{background:#f0f5fc;text-align:left;color:#465775}th,td{border:1px solid #e0e8f3;padding:8px}td input{padding:7px;min-width:65px}.right{text-align:right}.preview-head{display:flex;justify-content:space-between;align-items:center;gap:8px}.invoice-paper{border:1px solid #dce5f2;padding:22px;border-radius:8px;background:white}.invoice-title{display:flex;justify-content:space-between;gap:14px;border-bottom:2px solid #155eef;padding-bottom:14px}.invoice-title h3{margin:0 0 6px;font-size:23px;color:#155eef}.invoice-title p,.small{font-size:11px;color:#64748b;line-height:1.55}.billto{display:grid;grid-template-columns:1fr 1fr;gap:18px;padding:16px 0;font-size:12px}.totals{margin:14px 0 0 auto;max-width:270px;font-size:13px}.totalrow{display:flex;justify-content:space-between;padding:6px 0;border-bottom:1px solid #edf1f7}.grand{font-weight:850;color:#155eef;font-size:17px}.wa-note{background:#eafaf2;color:#17613b;border:1px solid #bdebd2;border-radius:8px;padding:11px;font-size:12px;line-height:1.5;margin-bottom:13px}.status{font-size:12px;margin-top:10px;min-height:18px}.bottomgrid{display:grid;grid-template-columns:1fr 1fr;gap:16px}.pill{display:inline-block;border-radius:20px;padding:4px 8px;background:#fff1d6;color:#8b5700;font-size:11px}.hidden{display:none!important}
@media(max-width:1100px){.layout{grid-template-columns:1fr}.stats{grid-template-columns:repeat(2,1fr)}.app{grid-template-columns:165px 1fr}}@media(max-width:700px){.app{display:block}aside{display:flex;overflow:auto;gap:4px;padding:8px}aside a{white-space:nowrap;margin:0}.main{padding:12px}.top{padding:14px}.brand{font-size:18px}.stats{gap:8px}.stat{padding:12px}.stat strong{font-size:20px}.formgrid{grid-template-columns:1fr}.field.full{grid-column:auto}.bottomgrid{grid-template-columns:1fr}.welcome{align-items:flex-start;flex-direction:column}.invoice-paper{padding:13px}.billto{gap:8px}}
@media print{.top,aside,.no-print,.stats,.welcome,.bottomgrid{display:none!important}.app{display:block}.main{padding:0}.layout{display:block}.layout>.panel:first-child{display:none}.panel{border:0;box-shadow:none;padding:0}.invoice-paper{border:0;padding:0}.preview-head{display:none}body{background:#fff}}
</style>
</head>
<body>
<header class="top"><div class="brand">▣ Invoice Generator<small>Simple • Fast • Professional</small></div><div id="todayLabel">All-in-One Business Toolkit</div></header>
<div class="app">
<aside class="no-print">
<a class="active" href="#dashboard">⌂ Dashboard</a><a href="#create">＋ Create Invoice</a><a href="#customer">♙ Customers</a><a href="#products">▣ Products & Services</a><a href="#payments">▤ Payments</a><a href="#reports">▥ Reports</a><a href="#settings">⚙ Settings</a>
</aside>
<main class="main">
<div class="welcome" id="dashboard"><div><h1>Invoice Workspace</h1><div class="muted">Create, preview, save, print, and share invoices with clients.</div></div><button class="btn primary no-print" onclick="newInvoice()">＋ New Invoice</button></div>
<div class="stats">
<div class="stat"><span>Total Invoices</span><strong id="statCount">0</strong><div class="muted">Saved in this browser</div></div>
<div class="stat"><span>Paid Invoices</span><strong id="statPaid">0</strong><div class="muted">Marked paid</div></div>
<div class="stat"><span>Unpaid Invoices</span><strong id="statUnpaid">0</strong><div class="muted">Awaiting payment</div></div>
<div class="stat"><span>Saved Invoice Value</span><strong id="statValue">₹0.00</strong><div class="muted">Total saved value</div></div>
</div>
<div class="layout">
<section class="panel" id="create">
<h2>Create Invoice <span class="muted">Live calculations</span></h2>
<div class="section">1. Business Information</div>
<div class="formgrid">
<div class="field"><label>Business / Seller Name *</label><input id="business" value="Your Business Name"></div>
<div class="field"><label>Phone</label><input id="businessPhone" placeholder="+91 98765 43210"></div>
<div class="field full"><label>Business Address</label><textarea id="businessAddress" placeholder="Street, city, state, postal code"></textarea></div>
<div class="field"><label>Email</label><input id="businessEmail" type="email" placeholder="you@example.com"></div>
<div class="field"><label>GSTIN / Tax ID (optional)</label><input id="gstin" placeholder="Tax registration number"></div>
<div class="field"><label>UPI ID / Payment instructions</label><input id="upi" placeholder="yourname@upi"></div>
<div class="field"><label>Invoice Currency</label><select id="currency" onchange="render()"><option value="INR">INR ₹</option><option value="USD">USD $</option><option value="GBP">GBP £</option><option value="EUR">EUR €</option></select></div>
</div>
<div class="section" id="customer">2. Client / Customer Details</div>
<div class="formgrid">
<div class="field"><label>Client / Company Name *</label><input id="client" placeholder="Client name" oninput="render()"></div>
<div class="field"><label>Client WhatsApp Number *</label><input id="whatsapp" placeholder="e.g. +91 98765 43210"></div>
<div class="field"><label>Client Email</label><input id="clientEmail" type="email" placeholder="client@example.com"></div>
<div class="field"><label>Client Tax ID (optional)</label><input id="clientTax" placeholder="GSTIN / Tax ID"></div>
<div class="field full"><label>Billing Address</label><textarea id="clientAddress" placeholder="Client billing address"></textarea></div>
</div>
<div class="section">3. Invoice Details</div>
<div class="formgrid">
<div class="field"><label>Invoice Number</label><input id="invoiceNo"></div>
<div class="field"><label>Invoice Date</label><input id="invoiceDate" type="date"></div>
<div class="field"><label>Due Date</label><input id="dueDate" type="date"></div>
<div class="field"><label>Payment Status</label><select id="paymentStatus" onchange="render()"><option value="Unpaid">Unpaid</option><option value="Paid">Paid</option><option value="Partially Paid">Partially Paid</option></select></div>
</div>
<div class="section" id="products">4. Products / Services</div>
<div class="items-wrap"><table id="editItems"><thead><tr><th>Item / Service</th><th>Description</th><th>Qty</th><th>Rate</th><th>Tax %</th><th></th></tr></thead><tbody id="itemRows"></tbody></table></div>
<div class="actions no-print"><button class="btn light" onclick="addItem()">＋ Add Item</button></div>
<div class="section">5. Discounts & Charges</div>
<div class="formgrid">
<div class="field"><label>Discount (%)</label><input id="discount" type="number" min="0" max="100" value="0" oninput="render()"></div>
<div class="field"><label>Shipping Charges</label><input id="shipping" type="number" min="0" value="0" oninput="render()"></div>
<div class="field"><label>Other Charges</label><input id="other" type="number" min="0" value="0" oninput="render()"></div>
<div class="field"><label>Amount Already Paid</label><input id="amountPaid" type="number" min="0" value="0" oninput="render()"></div>
</div>
<div class="section">6. Notes & Terms</div>
<div class="formgrid">
<div class="field"><label>Invoice Note</label><textarea id="notes">Thank you for your business!</textarea></div>
<div class="field"><label>Payment Terms</label><textarea id="terms">Please pay by the due date shown on this invoice.</textarea></div>
</div>
<div class="section" id="payments">7. Payment Information</div>
<div class="field"><label>Payment Instructions shown to client</label><textarea id="paymentInfo" placeholder="Bank details, UPI ID, payment link, etc."></textarea></div>
<div class="actions no-print"><button class="btn light" onclick="saveInvoice()">▣ Save Draft</button><button class="btn green" onclick="saveInvoice(true)">✓ Save Invoice</button><button class="btn light" onclick="newInvoice()">Reset</button></div>
<div id="saveStatus" class="status" role="status"></div>
</section>

<div>
<section class="panel" id="previewPanel">
<div class="preview-head"><h2>▤ Invoice Preview</h2><div class="actions no-print" style="margin:0"><button class="btn light" onclick="downloadInvoice()">↓ Download</button><button class="btn light" onclick="window.print()">⎙ Print / PDF</button></div></div>
<div class="invoice-paper" id="invoicePreview"></div>
</section>
<section class="panel no-print">
<h2>🟢 Send Invoice via WhatsApp</h2>
<div class="wa-note"><b>How sending works:</b> The button opens WhatsApp with the client number and a ready-to-send invoice summary. Review it and tap Send in WhatsApp. A normal website cannot silently send WhatsApp messages or attach PDFs automatically; fully automatic delivery requires a secure server and approved WhatsApp Business Platform API.</div>
<div class="field"><label>WhatsApp Number (include country code)</label><input id="waConfirm" placeholder="Example: 919876543210" oninput="document.getElementById('whatsapp').value=this.value"></div>
<div class="field" style="margin-top:10px"><label>Custom WhatsApp Message (optional)</label><textarea id="waMessage" placeholder="Hello, please find your invoice details below."></textarea></div>
<label style="display:flex;align-items:center;gap:8px;margin-top:10px"><input id="includePay" type="checkbox" checked style="width:auto"> Include payment instructions in message</label>
<div class="actions"><button class="btn green" style="width:100%;padding:13px" onclick="sendWhatsApp()">◉ Send Invoice to WhatsApp ↗</button></div>
<div id="waStatus" class="status" role="status"></div>
</section>
<section class="panel no-print" id="reports"><h2>Recent Saved Invoices <button class="btn light" onclick="exportCSV()">Export CSV</button></h2><div id="savedList" class="muted">No saved invoices yet.</div></section>
</div>
</div>
<div class="bottomgrid no-print">
<section class="panel"><h2>Quick Actions</h2><div class="actions"><button class="btn light" onclick="newInvoice()">＋ New Invoice</button><button class="btn light" onclick="document.getElementById('client').focus()">♙ Add Client</button><button class="btn light" onclick="addItem()">＋ Add Product</button><button class="btn light" onclick="exportCSV()">↓ Export CSV</button></div></section>
<section class="panel" id="settings"><h2>Settings & Data</h2><p class="muted">This starter version stores drafts in this browser only. Use Export CSV for a simple backup. For multi-device access, secure login, automatic WhatsApp delivery, and cloud backups, connect a backend database and WhatsApp Business Platform API.</p><button class="btn danger" onclick="clearSaved()">Clear Saved Invoices</button></section>
</div>
</main>
</div>
<script>
const $=id=>document.getElementById(id);
let items=[{name:'Service / Product',desc:'',qty:1,rate:0,tax:0}];
let saved=JSON.parse(localStorage.getItem('invoiceGeneratorSaved')||'[]');
const today=new Date(); const dateStr=d=>{const x=new Date(d.getTime()-d.getTimezoneOffset()*60000);return x.toISOString().slice(0,10)};
$('todayLabel').textContent=today.toLocaleDateString(undefined,{year:'numeric',month:'short',day:'numeric'});
$('invoiceDate').value=dateStr(today); let due=new Date();due.setDate(due.getDate()+7);$('dueDate').value=dateStr(due);$('invoiceNo').value='INV-'+today.getFullYear()+'-'+String(saved.length+1).padStart(4,'0');
function money(n){let c=$('currency').value;return new Intl.NumberFormat('en-IN',{style:'currency',currency:c,maximumFractionDigits:2}).format(Number(n)||0)}
function esc(s){return String(s??'').replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]))}
function addItem(){items.push({name:'',desc:'',qty:1,rate:0,tax:0});renderItems();render()}
function updateItem(i,k,v){items[i][k]=k==='name'||k==='desc'?v:(Number(v)||0);render()}
function removeItem(i){items.splice(i,1);if(!items.length)items.push({name:'',desc:'',qty:1,rate:0,tax:0});renderItems();render()}
function renderItems(){ $('itemRows').innerHTML=items.map((it,i)=>`<tr><td><input aria-label="Item name" value="${esc(it.name)}" oninput="updateItem(${i},'name',this.value)"></td><td><input aria-label="Description" value="${esc(it.desc)}" oninput="updateItem(${i},'desc',this.value)"></td><td><input aria-label="Quantity" type="number" min="0" value="${it.qty}" oninput="updateItem(${i},'qty',this.value)"></td><td><input aria-label="Rate" type="number" min="0" value="${it.rate}" oninput="updateItem(${i},'rate',this.value)"></td><td><input aria-label="Tax percent" type="number" min="0" max="100" value="${it.tax}" oninput="updateItem(${i},'tax',this.value)"></td><td><button class="btn danger" onclick="removeItem(${i})" aria-label="Remove item">×</button></td></tr>`).join('')}
function getData(){let subtotal=items.reduce((s,it)=>s+Math.max(0,it.qty)*Math.max(0,it.rate),0);let tax=items.reduce((s,it)=>s+Math.max(0,it.qty)*Math.max(0,it.rate)*Math.max(0,it.tax)/100,0);let discount=subtotal*Math.min(100,Math.max(0,Number($('discount').value)||0))/100;let shipping=Math.max(0,Number($('shipping').value)||0),other=Math.max(0,Number($('other').value)||0);let total=Math.max(0,subtotal+tax-discount+shipping+other);let paid=Math.max(0,Number($('amountPaid').value)||0);return {business:$('business').value,businessPhone:$('businessPhone').value,businessAddress:$('businessAddress').value,businessEmail:$('businessEmail').value,gstin:$('gstin').value,upi:$('upi').value,currency:$('currency').value,client:$('client').value,whatsapp:$('whatsapp').value,clientEmail:$('clientEmail').value,clientTax:$('clientTax').value,clientAddress:$('clientAddress').value,invoiceNo:$('invoiceNo').value,invoiceDate:$('invoiceDate').value,dueDate:$('dueDate').value,status:$('paymentStatus').value,items:JSON.parse(JSON.stringify(items)),subtotal,tax,discount,shipping,other,total,paid,balance:Math.max(0,total-paid),notes:$('notes').value,terms:$('terms').value,paymentInfo:$('paymentInfo').value}}
function render(){const d=getData();const rows=d.items.map((it,i)=>`<tr><td>${i+1}</td><td>${esc(it.name)}<div class="small">${esc(it.desc)}</div></td><td class="right">${it.qty}</td><td class="right">${money(it.rate)}</td><td class="right">${it.tax}%</td><td class="right">${money(it.qty*it.rate*(1+it.tax/100))}</td></tr>`).join('');$('invoicePreview').innerHTML=`<div class="invoice-title"><div><h3>${esc(d.business||'Your Business')}</h3><b>INVOICE</b><p>${esc(d.businessAddress).replace(/\n/g,'<br>')}<br>${esc(d.businessEmail)} ${d.businessPhone?'• '+esc(d.businessPhone):''}<br>${d.gstin?'Tax ID: '+esc(d.gstin):''}</p></div><div style="text-align:right"><b style="font-size:19px">${esc(d.invoiceNo||'INV-0001')}</b><p>Invoice date: ${esc(d.invoiceDate)}<br>Due date: ${esc(d.dueDate)}<br>Status: <b>${esc(d.status)}</b></p></div></div><div class="billto"><div><b>BILL TO</b><p>${esc(d.client||'Client Name')}<br>${esc(d.clientAddress).replace(/\n/g,'<br>')}<br>${esc(d.clientEmail)}<br>${d.clientTax?'Tax ID: '+esc(d.clientTax):''}</p></div><div><b>PAYMENT DETAILS</b><p>${esc(d.paymentInfo||d.upi||'Payment instructions not provided').replace(/\n/g,'<br>')}</p></div></div><div class="items-wrap"><table><thead><tr><th>#</th><th>Item / Description</th><th class="right">Qty</th><th class="right">Rate</th><th class="right">Tax</th><th class="right">Amount</th></tr></thead><tbody>${rows}</tbody></table></div><div class="totals"><div class="totalrow"><span>Subtotal</span><b>${money(d.subtotal)}</b></div><div class="totalrow"><span>Tax</span><b>${money(d.tax)}</b></div><div class="totalrow"><span>Discount</span><b>− ${money(d.discount)}</b></div><div class="totalrow"><span>Shipping</span><b>${money(d.shipping)}</b></div><div class="totalrow"><span>Other charges</span><b>${money(d.other)}</b></div><div class="totalrow grand"><span>Grand Total</span><b>${money(d.total)}</b></div><div class="totalrow"><span>Amount paid</span><b>${money(d.paid)}</b></div><div class="totalrow"><span>Balance due</span><b>${money(d.balance)}</b></div></div><div style="margin-top:24px;border-top:1px solid #e1e8f2;padding-top:12px"><b>Notes</b><p class="small">${esc(d.notes).replace(/\n/g,'<br>')}</p><b>Terms & Conditions</b><p class="small">${esc(d.terms).replace(/\n/g,'<br>')}</p><p class="small" style="text-align:center;margin-top:22px">Thank you for your business.</p></div>`;
}
function saveInvoice(mark=false){let d=getData();if(!d.client.trim()){ $('saveStatus').textContent='Please enter the client / company name before saving.'; $('client').focus();return}if(!d.invoiceNo.trim()){ $('saveStatus').textContent='Please enter an invoice number.';return}let idx=saved.findIndex(x=>x.invoiceNo===d.invoiceNo);if(idx>=0)saved[idx]=d;else saved.unshift(d);try{localStorage.setItem('invoiceGeneratorSaved',JSON.stringify(saved))}catch(e){$('saveStatus').textContent='Browser storage is full. Export your saved invoices before continuing.';return}$('saveStatus').textContent=mark?'Invoice saved successfully in this browser.':'Draft saved in this browser.';refreshSaved()}
function refreshSaved(){ $('statCount').textContent=saved.length;$('statPaid').textContent=saved.filter(x=>x.status==='Paid').length;$('statUnpaid').textContent=saved.filter(x=>x.status!=='Paid').length;$('statValue').textContent=money(saved.reduce((s,x)=>s+x.total,0));$('savedList').innerHTML=saved.length?`<div class="items-wrap"><table style="min-width:450px"><thead><tr><th>Invoice</th><th>Client</th><th>Amount</th><th>Status</th><th>Action</th></tr></thead><tbody>${saved.slice(0,20).map((x,i)=>`<tr><td>${esc(x.invoiceNo)}</td><td>${esc(x.client)}</td><td>${money(x.total)}</td><td><span class="pill">${esc(x.status)}</span></td><td><button class="btn light" onclick="loadSaved(${i})">Open</button></td></tr>`).join('')}</tbody></table></div>`:'No saved invoices yet.'}
function loadSaved(i){let d=saved[i];if(!d)return;for(let k of ['business','businessPhone','businessAddress','businessEmail','gstin','upi','currency','client','whatsapp','clientEmail','clientTax','clientAddress','invoiceNo','invoiceDate','dueDate','discount','shipping','other','amountPaid','notes','terms','paymentInfo'])if($(k)&&d[k]!==undefined)$(k).value=d[k];$('paymentStatus').value=d.status||'Unpaid';items=JSON.parse(JSON.stringify(d.items||[]));renderItems();render();window.scrollTo({top:0,behavior:'smooth'})}
function newInvoice(){if(!confirm('Start a new invoice? Unsaved changes will be lost.'))return;document.querySelectorAll('#create input, #create textarea').forEach(el=>{if(['discount','shipping','other','amountPaid'].includes(el.id))el.value=0;else if(el.type==='date')el.value='';else if(el.id==='invoiceNo')el.value='INV-'+new Date().getFullYear()+'-'+String(saved.length+1).padStart(4,'0');else if(el.id==='notes')el.value='Thank you for your business!';else if(el.id==='terms')el.value='Please pay by the due date shown on this invoice.';else if(el.id!=='business')el.value=''});$('currency').value='INR';$('paymentStatus').value='Unpaid';let now=new Date(),dd=new Date();dd.setDate(dd.getDate()+7);$('invoiceDate').value=dateStr(now);$('dueDate').value=dateStr(dd);items=[{name:'',desc:'',qty:1,rate:0,tax:0}];renderItems();render();$('saveStatus').textContent=''}
function normalizePhone(s){return String(s||'').replace(/\D/g,'')}
function sendWhatsApp(){const d=getData();const raw=$('waConfirm').value.trim()||d.whatsapp;const phone=normalizePhone(raw);if(!d.client.trim()){ $('waStatus').textContent='Please enter the client name first.';return}if(phone.length<8||phone.length>15){$('waStatus').textContent='Enter a valid WhatsApp number with country code, e.g. 919876543210.';return}const custom=$('waMessage').value.trim();const lines=[custom||`Hello ${d.client}, please find your invoice details below.`,`Invoice: ${d.invoiceNo}`,`Invoice date: ${d.invoiceDate}`,`Due date: ${d.dueDate}`,`Total: ${money(d.total)}`,`Amount paid: ${money(d.paid)}`,`Balance due: ${money(d.balance)}`,`Status: ${d.status}`];if($('includePay').checked&&(d.paymentInfo||d.upi))lines.push('Payment instructions: '+(d.paymentInfo||d.upi));lines.push('Thank you for your business!');const url='https://wa.me/'+phone+'?text='+encodeURIComponent(lines.join('\n'));$('waStatus').textContent='Opening WhatsApp. Review the message and press Send there. To include the actual PDF, download it first and attach it in WhatsApp.';window.open(url,'_blank','noopener,noreferrer')}
function downloadInvoice(){window.print()}
function exportCSV(){const all=saved.length?saved:[getData()];const cols=['invoiceNo','client','invoiceDate','dueDate','currency','subtotal','tax','discount','shipping','other','total','paid','balance','status','whatsapp'];const quote=v=>'"'+String(v??'').replace(/"/g,'""')+'"';const csv=[cols.join(','),...all.map(d=>cols.map(k=>quote(d[k])).join(','))].join('\r\n');const blob=new Blob([csv],{type:'text/csv;charset=utf-8;'});const a=document.createElement('a');a.href=URL.createObjectURL(blob);a.download='invoices.csv';a.click();URL.revokeObjectURL(a.href)}
function clearSaved(){if(!confirm('Delete all invoices saved in this browser? This cannot be undone.'))return;saved=[];localStorage.removeItem('invoiceGeneratorSaved');refreshSaved()}
renderItems();render();refreshSaved();
</script>
</body>
</html>
