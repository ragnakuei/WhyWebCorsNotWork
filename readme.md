# CORS 設定

#### WebAPI

Program.cs

```cs
var corsPolicyName = "AllowLocalHost7061";

builder.Services.AddCors(options =>
{
    options.AddPolicy(corsPolicyName, builder =>
    {
        builder.WithOrigins("https://localhost:7061")
               .WithMethods("Get");
    });
});

// ...

app.UseCors(corsPolicyName);
```


#### MVC

Views/Home/Index.cshtml

```html
<script>
fetch("https://localhost:7273/weatherforecast", {
    method: 'Get'
})
        .then(response => response.json())
        .then(data => console.table(data));
</script>
```
