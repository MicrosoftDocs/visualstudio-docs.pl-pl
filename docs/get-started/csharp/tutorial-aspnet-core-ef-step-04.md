---
title: Krok 4. Udostępnianie internetowego interfejsu API z poziomu aplikacji ASP.NET Core
description: Dodaj internetowy interfejs API do aplikacji internetowej ASP.NET Core, korzystając z tego samouczka wideo, i instrukcje krok po kroku.
ms.custom: get-started
ms.date: 02/13/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 9a2ee576808698e19726cadfea7ba560ce3bdb7c
ms.sourcegitcommit: a778dffddb05d2f0f15969eadaf9081c9b466196
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2020
ms.locfileid: "91780942"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>Krok 4. Uwidacznianie internetowego interfejsu API w aplikacji ASP.NET Core

Wykonaj następujące kroki, aby dodać internetowy interfejs API do istniejącej aplikacji ASP.NET Core.

_Obejrzyj ten film wideo i postępuj zgodnie z instrukcjami, aby dodać obsługę internetowego interfejsu API do swojej pierwszej aplikacji ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>Otwórz projekt

Otwórz aplikację ASP.NET Core w programie Visual Studio 2019. Aplikacja powinna już używać EF Core do zarządzania typami modeli zgodnie z konfiguracją w [kroku 3 tej serii samouczków](tutorial-aspnet-core-ef-step-03.md).

## <a name="add-an-api-controller"></a>Dodawanie kontrolera interfejsu API

Kliknij prawym przyciskiem myszy projekt i Dodaj nowy folder o nazwie *API*. Następnie kliknij prawym przyciskiem myszy ten folder i wybierz polecenie **Dodaj**  >  **nowy element szkieletowy**. Wybierz pozycję **kontroler interfejsu API z akcjami przy użyciu Entity Framework.** Teraz wybierz istniejącą klasę modelu i kliknij przycisk **Dodaj**.

![Kontroler interfejsu API programu Visual Studio 2019 ASP.NET Core](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>Przeglądanie wygenerowanego kontrolera

Wygenerowany kod zawiera nową klasę kontrolera. W górnej części definicji klasy są dwa atrybuty.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

Pierwszy z nich określa trasę dla akcji w tym kontrolerze, co oznacza, że `api/[controller]` kontroler ma nazwę `GamesController` trasy `api/Games` .

Drugi atrybut, `[ApiController]` ,,,, dodaje przydatne walidacje do klasy, na przykład upewniając się, że każda metoda akcji zawiera własny `[Route]` atrybut.

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

Kontroler używa istniejącego `AppDbContext` , przekazaną do jego konstruktora. Każda akcja będzie używać tego pola do pracy z danymi aplikacji.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

Pierwsza metoda to proste żądanie GET określone przy użyciu `[HttpGet]` atrybutu. Nie przyjmuje parametrów i zwraca listę wszystkich gier w bazie danych.

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

Następna Metoda określa `{id}` w trasie, która zostanie dodana do trasy następującej po, `/` tak aby cała trasa była taka, `api/Games/5` jak pokazano w komentarzu w górnej części ekranu. `id`Dane wejściowe są mapowane na `id` parametr metody. Wewnątrz metody, jeśli model jest nieprawidłowy, `BadRequest` zwracany jest wynik. W przeciwnym razie Dr podejmie próbę znalezienia rekordu pasującego do podanego `id` . Jeśli nie można `NotFound` zwrócić wyniku, w przeciwnym razie `Game` zwracany jest odpowiedni rekord.

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

Następnie `[HttpPut]` do przeprowadzenia aktualizacji jest używane żądanie wysłane do interfejsu API. Nowy `Game` rekord jest podany w treści żądania. Wykonywane jest pewne sprawdzanie poprawności i sprawdzanie błędów. Jeśli wszystko się powiedzie, rekord w bazie danych zostanie zaktualizowany wartościami podanymi w treści żądania. W przeciwnym razie zwracana jest odpowiednia odpowiedź na błąd.

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

`[HttpPost]`Żądanie służy do dodawania nowych rekordów do systemu. Podobnie jak w przypadku `[HttpPut]` , rekord zostanie dodany w treści żądania. Jeśli jest on prawidłowy, EF Core dodaje rekord do bazy danych, a akcja zwróci zaktualizowany rekord (z wygenerowanym IDENTYFIKATORem bazy danych) i link do rekordu w interfejsie API.

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

`[HttpDelete]`Na koniec trasa jest używana z identyfikatorem do usunięcia rekordu. Jeśli żądanie jest prawidłowe i istnieje rekord o podanym IDENTYFIKATORze, EF Core usunąć go z bazy danych.

## <a name="adding-swagger"></a>Dodawanie struktury Swagger

Swagger to dokumentacja interfejsu API i narzędzie do testowania, które można dodać jako zestaw usług i oprogramowania pośredniczącego do aplikacji ASP.NET Core. Aby to zrobić, kliknij prawym przyciskiem myszy projekt i wybierz polecenie **Zarządzaj pakietami NuGet**. Następnie kliknij przycisk **Przeglądaj**, Wyszukaj `Swashbuckle.AspNetCore` i Zainstaluj wersję 4.0.1.

![Program Visual Studio 2019 Add Swashbuckle z narzędzia NuGet](media/vs-2019/vs2019-nuget-swashbuckle.png)

Po zainstalowaniu programu Otwórz `Startup.cs` i Dodaj następujący na końcu `ConfigureServices` metody:

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

Należy również dodać `using Swashbuckle.AspNetCore.Swagger;` w górnej części pliku.

Następnie Dodaj następujące elementy do `Configure` metody, tuż przed `UseMvc` :

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

Teraz powinno być możliwe skompilowanie i uruchomienie aplikacji. W przeglądarce przejdź do na `/swagger` pasku adresu. Powinna zostać wyświetlona lista punktów końcowych i modeli interfejsu API aplikacji.

![Strona struktury Swagger programu Visual Studio 2019 w przeglądarce](media/vs-2019/vs2019-swagger-browser.png)

Kliknij punkt końcowy w obszarze gry, `Try it out` a następnie, `Execute` Aby zobaczyć, jak działają różne punkty końcowe.

## <a name="next-steps"></a>Następne kroki

W następnym filmie wideo dowiesz się, jak wdrożyć aplikację na platformie Azure.

[Krok 5. wdrażanie aplikacji ASP.NET Core na platformie Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie z Swashbuckle i ASP.NET Core](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio&preserve-view=true)
- [ASP.NET Core stronach pomocy interfejsu API sieci Web w programie Swagger/OpenAPI](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2&preserve-view=true)