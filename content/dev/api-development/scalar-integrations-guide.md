---
tags:
- api-development
- backend
- frontend
- openapi
- scalar
---

# 🌐 Scalar Integrations: Enhancing API Development Across Frameworks

Scalar provides seamless integrations with various frameworks and platforms, making API development easier and more efficient. It supports a wide range of technologies, including backend frameworks and frontend tools for documentation.

---

## 🔍 Overview

Scalar is designed to simplify API development by offering robust support for various frameworks and technologies. It integrates smoothly with both backend frameworks and frontend documentation tools, enabling a unified development experience.

---

## 🧠 Supported Integrations

Scalar supports numerous backend frameworks and frontend tools:

### 🔧 Backend Frameworks

- **.NET**
    
- **Nitro**
    
- **Platformatic**
    
- **FastAPI**
    
- **Hono**
    
- **NestJS**
    
- **Nuxt**
    
- **Rust**
    
- **AdonisJS**
    
- **Elysia**
    
- **Express**
    
- **Fastify**
    
- **GO**
    
- **Laravel**
    
- **Litestar**
    
- **Next.js**
    

### 📄 Frontend & Documentation

- **HTML**
    
- **React**
    
- **Vue.js**
    
- **Docusaurus**
    

---

## ⚙️ Installation

To install Scalar in a **.NET** project, run the following command:

```bash
dotnet add package Scalar.AspNetCore
```

For other frameworks, check the [official Scalar documentation](https://scalar.com/#integrations).

---

## 🛠️ Usage Example

Here’s a basic example of using Scalar with **.NET**:

```csharp
using Scalar.AspNetCore;

var builder = WebApplication.CreateBuilder();

builder.Services.AddOpenApi();

var app = builder.Build();

app.MapOpenApi();

if (app.Environment.IsDevelopment())
{
    app.MapScalarApiReference();
}

app.MapGet("/", () => "Hello world!");

app.Run();
```

---

## 🌍 OpenAPI Support

Once Scalar is integrated, you can:

- **Import JSON**: Use the generated OpenAPI JSON in the [Scalar Client](https://chatgpt.com/c/Scalar%20API%20Client) or [Scalar Docs](https://chatgpt.com/c/Scalar%20Dashboard) for better API exploration.
    
- **Download OpenAPI JSON**: Export the OpenAPI specification to integrate with third-party tools or documentation platforms.
    

---

## 📚 Prebuilt Examples

For ready-to-use implementations in different frameworks, check out the [Scalar API Examples Repository](https://github.com/ClementBobin/Api):

- [Fastify](https://github.com/ClementBobin/Api/tree/FastifyPrisma)
    
- [Express](https://github.com/ClementBobin/Api/tree/ExpressPrisma)
    
- [NextJS](https://github.com/ClementBobin/Api/tree/NextJsPrisma)
    
- [Laravel](https://github.com/ClementBobin/Api/tree/Laravel)
    

For additional integrations, visit the official [Scalar Integrations Page](https://scalar.com/#integrations).

---

## ⚖️ Security and Ethical Considerations

> [!warning]  
> When using Scalar, always ensure you follow best practices for authentication, authorization, and data security. Ensure your API specifications and documentation adhere to privacy regulations and security standards.

- **Authentication**: Use secure methods such as OAuth or JWT for authentication.
    
- **Authorization**: Implement granular permissions for API access.
    
- **Data Privacy**: Ensure sensitive data is encrypted and stored securely.
    

---

## 📚 Conclusion

Scalar streamlines the process of developing, documenting, and managing APIs by integrating with a wide variety of backend frameworks and frontend documentation tools. It supports seamless OpenAPI integration, making it a powerful tool for any API project.

---

## 📚 Resources

- [Official Scalar Website](https://scalar.com/)
    
- [Scalar Documentation](https://scalar.com/docs/)
    
- [Scalar Integrations](https://scalar.com/#integrations)
    

---

## 🌍 Explore More

- **[API Documentation Best Practices](https://www.example.com/api-doc-best-practices)** — Discover more about creating high-quality API documentation.
    
- **[Framework-Specific Tutorials](https://www.example.com/framework-tutorials)** — Learn how to integrate Scalar with various backend frameworks.
    
---

Scalar simplifies and accelerates API development and documentation by integrating with popular backend frameworks and frontend tools, enabling developers to create and manage APIs more efficiently.