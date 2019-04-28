---
title: Krok 4. Udostępnianie internetowego interfejsu API z Twojej aplikacji platformy ASP.NET Core
description: Dodawanie interfejsu API sieci web do aplikacji internetowej ASP.NET Core za pomocą tego samouczka wideo, a instrukcje krok po kroku.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 93e3b0af04060c3a3805b29e5d1da71c4f60ec31
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62553881"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>Krok 4. Udostępnianie internetowego interfejsu API z poziomu aplikacji ASP.NET Core

Wykonaj następujące kroki, aby dodać interfejs API sieci web do istniejącej aplikacji platformy ASP.NET Core.

_Obejrzyj ten film wideo i spróbuj dodać obsługę interfejsu API sieci web do pierwszej aplikacji ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>Otwórz projekt

Otwórz aplikację platformy ASP.NET Core w programie Visual Studio 2019 r. Aplikacja powinna już używać programu EF Core Zarządzanie swój typ modelu zgodnie z konfiguracją w [krok 3 z tej serii samouczków](tutorial-aspnet-core-ef-step-03.md).

## <a name="add-an-api-controller"></a>Dodaj Kontroler interfejsu API

Kliknij prawym przyciskiem myszy projekt i Dodaj nowy folder o nazwie *Api*. Następnie, w tym folderze kliknij prawym przyciskiem myszy i wybierz polecenie **Dodaj** > **nowy element szkieletu**. Wybierz **Kontroler interfejsu API z akcjami używający narzędzia Entity Framework.** Teraz wybierz istniejącą klasę modelu i kliknij przycisk **Dodaj**.

![Visual Studio 2019 platformy ASP.NET Core szkieletu kontrolera interfejsu API](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>Przeglądanie wygenerowanym kontrolerze

Wygenerowany kod zawiera nową klasę kontrolera. W górnej części definicji klasy są dwa atrybuty.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

Pierwsza z nich Określa trasy dla akcji, w tym kontrolerze jako `api/[controller]` co oznacza, że jeśli kontroler ma nazwę `GamesController` będzie trasy `api/Games`.

Drugi atrybut `[ApiController]`, dodaje pewne przydatne sprawdzania poprawności do klasy, takie jak zapewnienie każdej akcji metoda zawiera swój własny `[Route]` atrybutu.

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

Kontroler jest używany istniejący `AppDbContext`, przekazana do jej konstruktora. Każda akcja użyje tego pola do pracy z danymi aplikacji.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

Pierwsza metoda jest proste żądania GET, jak przy użyciu określonego `[HttpGet]` atrybutu. Go nie przyjmuje żadnych parametrów i zwraca listę wszystkich gier w bazie danych.

```csharp
// GET: api/Games/5
[HttpGet("{id}")]
public async Task<IActionResult> GetGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);

    if (game == null)
    {
        return NotFound();
    }

    return Ok(game);
}
```

Następna metoda Określa `{id}` w trasie, które zostaną dodane do następujących tras `/` dzięki pełnej trasy będzie to wyglądać `api/Games/5` pokazany w komentarzu u góry. `id` Danych wejściowych jest mapowany na `id` parametrem w metodzie. Wewnątrz metody, jeśli model jest nieprawidłowy `BadRequest` zostanie zwrócony wynik. W przeciwnym razie EF spróbuje znaleźć rekordów pasujących do podanych `id`. Jeśli jest ona nieosiągalna `NotFound` zostanie zwrócony wynik, w przeciwnym razie odpowiednie `Game` zwracany rekord.

```csharp
// PUT: api/Games/5
[HttpPut("{id}")]
public async Task<IActionResult> PutGame([FromRoute] int id, [FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    if (id != game.Id)
    {
        return BadRequest();
    }

    _context.Entry(game).State = EntityState.Modified;

    try
    {
        await _context.SaveChangesAsync();
    }
    catch (DbUpdateConcurrencyException)
    {
        if (!GameExists(id))
        {
            return NotFound();
        }
        else
        {
            throw;
        }
    }

    return NoContent();
}
```

Następnie `[HttpPut]` żądania skierowane do interfejsu API jest używany do wykonywania aktualizacji. Nowy `Game` rekordu znajduje się w treści żądania. Niektóre weryfikacji i sprawdzania błędów jest wykonywane, a jeśli wszystko jest pomyślne rekord w bazie danych jest aktualizowany przy użyciu wartości podanych w treści żądania. W przeciwnym razie zwracana jest odpowiedź odpowiedni komunikat o błędzie.

```csharp
// POST: api/Games
[HttpPost]
public async Task<IActionResult> PostGame([FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    _context.Game.Add(game);
    await _context.SaveChangesAsync();

    return CreatedAtAction("GetGame", new { id = game.Id }, game);
}
```

`[HttpPost]` Żądania jest używana do dodawania nowych rekordów do systemu. Podobnie jak w przypadku `[HttpPut]`, rekord zostanie dodany do treści żądania. Jeśli jest on prawidłowy, programem EF Core dodaje rekord do bazy danych i akcji zwraca zaktualizowanym rekordem (za pomocą jego Identyfikatora bazy danych, wygenerowane) oraz link do rekordu w interfejsie API.

```csharp
// DELETE: api/Games/5
[HttpDelete("{id}")]
public async Task<IActionResult> DeleteGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);
    if (game == null)
    {
        return NotFound();
    }

    _context.Game.Remove(game);
    await _context.SaveChangesAsync();

    return Ok(game);
}
```

Na koniec `[HttpDelete]` używana jest trasa o identyfikatorze Aby usunąć rekord. Jeśli żądanie jest prawidłowe, i istnieje rekord o podanym identyfikatorze, EF Core go usunąć z bazy danych.

## <a name="adding-swagger"></a>Dodawanie programu Swagger

Struktury swagger jest dokumentacji interfejsu API i narzędzia testowania, które można dodać do aplikacji ASP.NET Core jako zestaw usług i oprogramowania pośredniczącego. Aby to zrobić, kliknij prawym przyciskiem myszy nad projektem i wybierz polecenie **Zarządzaj pakietami NuGet**. Kliknij pozycję **Przeglądaj** i wyszukaj `Swashbuckle.AspNetCore` i zainstalowania odpowiedniego pakietu.

![Visual Studio 2019 Dodaj Swashbuckle z pakietów Nuget](media/vs-2019/vs2019-nuget-swashbuckle.png)

Po zainstalowaniu Otwórz `Startup.cs` i Dodaj następujący element do końca `ConfigureServices` metody:

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

Należy także dodać `using Swashbuckle.AspNetCore.Swagger;` w górnej części pliku.

Następnie dodaj następujące polecenie, aby `Configure` metody, tuż przed `UseMvc`:

```csharp
// Enable middleware to serve generated Swagger as a JSON endpoint.
app.UseSwagger();

// Enable middleware to serve swagger-ui (HTML, JS, CSS, etc.), 
// specifying the Swagger JSON endpoint.
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
});
```

Teraz można skompilować i uruchomić aplikację. W przeglądarce przejdź do `/swagger` na pasku adresu. Powinien zostać wyświetlony listy punktów końcowych interfejsu API Twojej aplikacji i modeli. 

![Visual Studio 2019 struktury Swagger strony w przeglądarce](media/vs-2019/vs2019-swagger-browser.png)

Kliknij punkt końcowy w ramach gry, a następnie `Try it out` i `Execute` aby zobaczyć, jak działają różne punkty końcowe.

## <a name="next-steps"></a>Następne kroki

W następnym filmie wideo dowiesz się, jak wdrożyć aplikację na platformie Azure.

[Krok 5. Wdrażanie aplikacji platformy ASP.NET Core na platformie Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do pakietu Swashbuckle i ASP.NET Core](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio)
- [Strony sieci web platformy ASP.NET Core pomocy interfejsu API, w strukturze Swagger / interfejsu OpenAPI](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2)