## EmailJS Cheat-Sheet

EmailJS is a service that allows you to send emails directly from client-side JavaScript applications. It simplifies the process of sending transactional emails, such as contact form submissions, welcome messages, and notifications. This cheat-sheet covers the fundamental steps to use EmailJS to send emails from your web application.

### Installation

1. First, sign up for an account on the [EmailJS website](https://www.emailjs.com/).
    
2. Install the EmailJS client library using npm or yarn:
    

```bash
npm install emailjs-com
```

### Setup EmailJS Account

1. After signing up, log in to your EmailJS account and create a new email service.
    
2. Configure the email template with placeholders for dynamic content, like recipient names or message content.
    
3. Obtain your EmailJS user ID and service ID from the EmailJS dashboard.
    

### Sending an Email

1. Import and initialize EmailJS in your JavaScript file:

```jsx
import emailjs from 'emailjs-com';  
emailjs.init('your_user_id');
```

2. Define the parameters for the email template and send the email:

```js
const templateParams = {   
	from_name: 'John Doe',   
	to_name: 'Jane Doe',   
	message: 'Hello, Jane! This is a test email from EmailJS.', 
};  
emailjs.send('your_service_id', 'your_template_id', templateParams)   .then((response) => {     
	console.log('Email sent successfully:', response.text);   
})   
.catch((error) => {     
	console.error('Error sending email:', error);   
});
```

In this example, replace `'your_user_id'`, `'your_service_id'`, and `'your_template_id'` with your actual EmailJS user ID, service ID, and template ID, respectively.

### Dynamic Content

1. You can use placeholders in the email template to replace them with dynamic content:

```js
const templateParams = {   
	from_name: 'John Doe',   
	to_name: 'Jane Doe',   
	message: 'Hello, Jane! This is a test email from EmailJS.', 
};
```

In this example, the template uses placeholders like `{from_name}`, `{to_name}`, and `{message}`.

### Email Templates

1. Create an email template on the EmailJS dashboard with the desired content and placeholders.
    
2. Make sure to define the same placeholders in the `templateParams` object in your JavaScript code.
    

### Customization

1. Customize the email subject, body, and other parameters based on your application's needs.
    
2. Use email service providers like Gmail, Outlook, or others to send emails through EmailJS.
    

### Real life exemple

Here the code let you create a form, and send it with custom

```jsx
import React, { useRef, useState } from "react"; 
import emailjs from "emailjs-com"; 

const Contact = () => { 
	const formRef = useRef(); 
	const [form, setForm] = useState({ 
		name: "", 
		email: "", 
		message: "", 
	}); 
	
	const [loading, setLoading] = useState(false); 
	
	const handleChange = (e) => { 
		const { target } = e; 
		const { name, value } = target; 
		
		setForm({ 
			...form, 
			[name]: value, 
		}); 
	}; 
	
	const handleSubmit = (e) => { 
		e.preventDefault(); 
		setLoading(true); 
		
		emailjs 
			.send( 
				"your_service_id", 
				"your_template_id", 
				{ 
					from_name: form.name, 
					to_name: "Clement Bobin", 
					from_email: form.email, 
					to_email: "clementbobin21@gmail.com", 
					message: form.message, 
				}, 
				"your_user_id" 
			) 
			.then( 
				() => { 
					setLoading(false); 
					alert("Thank you. I will get back to you as soon as possible."); 
					setForm({ 
						name: "", 
						email: "", 
						message: "", 
					}); 
				}, 
				(error) => { 
					setLoading(false); 
					console.error(error); 
					alert("Ahh, something went wrong. Please try again."); 
				} 
			); 
	}; 
	
	return ( 
		<div> 
			<form ref={formRef} onSubmit={handleSubmit} className='mt-12 flex flex-col gap-8' > 
				<label className='flex flex-col'> 
					<span className='text-white font-medium mb-4'>Your Name</span> 
					<input type='text' name='name' value={form.name} onChange={handleChange} placeholder="What's your good name?" className='bg-tertiary py-4 px-6 placeholder:text-secondary text-white rounded-lg outline-none border-none font-medium' /> 
				</label> 
				<label className='flex flex-col'> 
					<span className='text-white font-medium mb-4'>Your email</span> 
					<input type='email' name='email' value={form.email} onChange={handleChange} placeholder="What's your web address?" className='bg-tertiary py-4 px-6 placeholder:text-secondary text-white rounded-lg outline-none border-none font-medium' /> 
				</label> 
				<label className='flex flex-col'> 
					<span className='text-white font-medium mb-4'>Your Message</span> 
					<textarea rows={7} name='message' value={form.message} onChange={handleChange} placeholder='What you want to say?' className='bg-tertiary py-4 px-6 placeholder:text-secondary text-white rounded-lg outline-none border-none font-medium' /> 
				</label> 
				<button type='submit' className='bg-tertiary py-3 px-8 rounded-xl outline-none w-fit text-white font-bold shadow-md shadow-primary' > 
					{loading ? "Sending..." : "Send"} 
				</button> 
			</form> 
		</div> 
	); 
}; 

export default Contact;
```

### Conclusion

This cheat-sheet covers the basic usage of EmailJS to send emails directly from client-side JavaScript applications. EmailJS simplifies the process of sending transactional emails, making it easier to handle email communications in your web application. For more advanced features and detailed documentation, refer to the official EmailJS documentation. Happy emailing!