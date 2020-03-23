---
title: 'Krok 4: Udostępnianie internetowego interfejsu API z aplikacji ASP.NET Core'
description: Dodaj internetowy interfejs API do aplikacji ASP.NET Core Web App za pomocą tego samouczka wideo i instrukcji krok po kroku.
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
ms.openlocfilehash: 5ea9468bdf86986ab542fb1cabc873c9aeb75fd6
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580037"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>Krok 4: Uwidacznianie internetowego interfejsu API z aplikacji ASP.NET Core

Wykonaj następujące kroki, aby dodać internetowy interfejs API do istniejącej aplikacji ASP.NET Core.

_Obejrzyj ten klip wideo i obserwuj, aby dodać obsługę interfejsu API w sieci Web do pierwszej aplikacji ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>Otwórz swój projekt

Otwórz aplikację ASP.NET Core w programie Visual Studio 2019. Aplikacja powinna już używać EF Core do zarządzania typami modeli, zgodnie z konfiguracją w [kroku 3 tej serii samouczków](tutorial-aspnet-core-ef-step-03.md).

## <a name="add-an-api-controller"></a>Dodawanie kontrolera interfejsu API

Kliknij prawym przyciskiem myszy projekt i dodaj nowy folder o nazwie *Api*. Następnie kliknij prawym przyciskiem myszy ten folder i wybierz pozycję **Dodaj** > **nowy element rusztowania**. Wybierz **kontroler interfejsu API z akcjami przy użyciu entity framework.** Teraz wybierz istniejącą klasę modelu i kliknij przycisk **Dodaj**.

![Kontroler interfejsu API ASP.NET rdzenia szkieletowego programu Visual Studio 2019](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>Przeglądanie wygenerowanego kontrolera

Wygenerowany kod zawiera nową klasę kontrolera. W górnej części definicji klasy są dwa atrybuty.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

Pierwszy z nich określa trasę dla akcji `api/[controller]` w tym kontrolerze `GamesController` jako będącą, co oznacza, że jeśli kontroler zostanie nazwany, trasa będzie `api/Games`.

Drugi atrybut, `[ApiController]`, dodaje kilka przydatnych sprawdzania poprawności do klasy, takich `[Route]` jak zapewnienie, że każda metoda akcji zawiera własny atrybut.

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

Kontroler używa istniejącego `AppDbContext`, przeszedł do jego konstruktora. Każda akcja użyje tego pola do pracy z danymi aplikacji.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

Pierwsza metoda jest proste żądanie GET, `[HttpGet]` jak określono przy użyciu atrybutu. Nie wymaga żadnych parametrów i zwraca listę wszystkich gier w bazie danych.

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

Następna metoda `{id}` określa w trasie, która zostanie dodana `/` do trasy po tak `api/Games/5` pełna trasa będzie coś takiego jak pokazano w komentarzu u góry. Dane `id` wejściowe są `id` mapowane na parametr w metodzie. Wewnątrz metody, jeśli model jest `BadRequest` nieprawidłowy, zwracany jest wynik. W przeciwnym razie EF spróbuje znaleźć `id`rekord pasujący do podanego . Jeśli nie można `NotFound` zwracać wyniku, w `Game` przeciwnym razie zwracany jest odpowiedni rekord.

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

Następnie żądanie `[HttpPut]` wykonane do interfejsu API jest używany do wykonywania aktualizacji. Nowy `Game` rekord znajduje się w treści żądania. Niektóre sprawdzanie poprawności i sprawdzanie błędów jest wykonywane, a jeśli wszystko zakończy się pomyślnie rekord w bazie danych jest aktualizowany o wartości podane w treści żądania. W przeciwnym razie zwracana jest odpowiednia odpowiedź na błąd.

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

Żądanie `[HttpPost]` służy do dodawania nowych rekordów do systemu. Podobnie jak `[HttpPut]`w tym , rekord jest dodawany w treści żądania. Jeśli jest prawidłowy, EF Core dodaje rekord do bazy danych, a akcja zwraca zaktualizowany rekord (z jego identyfikatorem wygenerowanym bazy danych) i łącze do rekordu w interfejsie API.

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

Na koniec `[HttpDelete]` trasa jest używana z identyfikatorem, aby usunąć rekord. Jeśli żądanie jest prawidłowe i istnieje rekord o podanym identyfikatorze, EF Core usuń go z bazy danych.

## <a name="adding-swagger"></a>Dodawanie Swagger

Swagger to narzędzie do dokumentacji i testowania interfejsu API, które można dodać jako zestaw usług i oprogramowania pośredniczącego do aplikacji ASP.NET Core. Aby to zrobić, kliknij prawym przyciskiem myszy projekt i wybierz pozycję **Zarządzaj pakietami NuGet**. Następnie kliknij przycisk **Przeglądaj**, wyszukaj `Swashbuckle.AspNetCore`i zainstaluj wersję 4.0.1.

![Visual Studio 2019 Dodaj swashbuckle z Nuget](media/vs-2019/vs2019-nuget-swashbuckle.png)

Po zainstalowaniu `Startup.cs` otwórz i dodaj następujące `ConfigureServices` elementy na końcu metody:

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

Musisz również dodać `using Swashbuckle.AspNetCore.Swagger;` w górnej części pliku.

Następnie dodaj następujące elementy `Configure` do metody, tuż przed: `UseMvc`

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

Teraz powinieneś być w stanie skompilować i uruchomić aplikację. W przeglądarce przejdź `/swagger` do paska adresu. Powinna zostać wyświetlona lista punktów końcowych i modeli interfejsu API aplikacji. 

![Strona Swagger programu Visual Studio 2019 w przeglądarce](media/vs-2019/vs2019-swagger-browser.png)

Kliknij punkt końcowy w `Try it out` obszarze `Execute` Gry, a następnie, aby zobaczyć, jak zachowują się różne punkty końcowe.

## <a name="next-steps"></a>Następne kroki

W następnym klipie wideo dowiesz się, jak wdrożyć aplikację na platformie Azure.

[Krok 5: Wdrażanie aplikacji ASP.NET Core na platformie Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>Zobacz też

- [Pierwsze kroki z Swashbuckle i ASP.NET Core](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio)
- [ASP.NET Core web API strony pomocy z Swagger / OpenAPI](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2)