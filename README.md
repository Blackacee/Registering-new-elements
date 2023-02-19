# Registering-new-elements

const InitiallyHiddenElement = document.registerElement('initially-hidden', class extends
HTMLElement {
 createdCallback() {
 this.revealTimeoutId = null;
 }
 attachedCallback() {
 const seconds = Number(this.getAttribute('for'));
 this.style.display = 'none';
 this.revealTimeoutId = setTimeout(() => {
 this.style.display = 'block';
 }, seconds * 1000);
 }
 detachedCallback() {
 if (this.revealTimeoutId) {
 clearTimeout(this.revealTimeoutId);
 this.revealTimeoutId = null;
 }
 }
});
<initially-hidden for="2">Hello</initially-hidden>
<initially-hidden for="5">World</initially-hidden>
