# Execute XSS attack inside an Angular App

- Make sure you followed the steps in `00_Setup.md`
- Now we want to inject some malicious JavaScript - By clicking on Tab 'Book' we'll find another Button 'Create Book'. Now we have some Input fields to insert Code into.
- Inject following malicious JavaScript inside the `Abstract`-Input field: `<iframe src="javascript:alert('xss')">`
- Investigate the Angular Code - Do you know how the attack could happen?
