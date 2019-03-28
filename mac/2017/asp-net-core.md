---
title: Wprowadzenie do platformy ASP.NET Core
description: W tym artykule opisano sposób rozpoczęcia pracy z programem ASP.NET w programie Visual Studio dla komputerów Mac, w tym instalacji i tworzenia nowego projektu.
author: conceptdev
ms.author: crdun
ms.date: 07/13/2017
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
ms.openlocfilehash: 7544d3aa72bb981a35b3c7fc63db3f397f8f26dd
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58573028"
---
# <a name="getting-started-with-aspnet-core"></a>Wprowadzenie do platformy ASP.NET Core

 Visual Studio dla komputerów Mac ułatwia opracowywanie usługi aplikacji z obsługą jej na najnowsze platformy tworzenia aplikacji sieci Web platformy ASP.NET Core. Platforma ASP.NET Core jest uruchamiany na platformie .NET Core, najnowsze zmiany w .NET Framework i środowiska uruchomieniowego. Go ma pod kątem wysoka wydajność, brana pod uwagę w przypadku instalacji małych rozmiarów i obraz do uruchomienia w systemie Linux i macOS, a także Windows.

## <a name="installing-net-core"></a>Instalowanie platformy .NET Core

.NET core 1.1 jest automatycznie instalowany podczas instalowania programu Visual Studio dla komputerów Mac.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Tworzenie aplikacji ASP.NET Core w programie Visual Studio dla komputerów Mac

Open Visual Studio for Mac. Na stronie powitalnej zaznacz **nowy projekt...**

![Okno dialogowe nowego projektu](media/asp-net-core-image1.png)

Spowoduje to wyświetlenie okna dialogowego Nowy projekt, dzięki czemu można wybrać szablon do tworzenia aplikacji.

Istnieje wiele projektów, które udostępnia wstępnie utworzonego szablonu, aby rozpocząć tworzenie aplikacji ASP.NET Core. Są to:

- **.NET core > Aplikacja pusty sieci Web platformy ASP.NET Core**
- **.NET core > Aplikacja sieci Web platformy ASP.NET Core**
- **.NET core > Interfejs API sieci Web platformy ASP.NET Core**
- **Dla wielu platform > aplikacji > połączonych aplikacji**

![ASP.NET Project Options](media/asp-net-core-image11.png)

Wybierz **pusta aplikacja sieci Web platformy ASP.NET Core** i naciśnij klawisz **dalej**. Należy nadać projektowi nazwę i naciśnij klawisz **Utwórz**. Spowoduje to utworzenie nowej aplikacji platformy ASP.NET Core, która powinna wyglądać podobnie do poniższej ilustracji:

![Nowy widok pusty projekt programu ASP.NET Core](media/asp-net-core-image4.png)

Pusta aplikacja sieci Web platformy ASP.NET Core tworzy aplikację sieci web z dwóch domyślnych plików: **Plik program.cs** i **Startup.cs**, które zostały wyjaśnione poniżej. Tworzy również folder Dependencies, która zawiera zależności pakietów NuGet projektu, takich jak ASP.NET Core, w ramach platformy .NET Core i docelowych elementów MSBuild, które są kompilowane w projekcie:

![Konsola rozwiązania wyświetlanie zależności](media/asp-net-core-image12.png)

### <a name="programcs"></a>Program.cs

Otwórz i sprawdź **Program.cs** plik w projekcie. Należy zauważyć, że w mają miejsce dwie rzeczy `Main` metodą — wpis w swojej aplikacji:

```csharp
public static void Main(string[] args)
{
    var host = new WebHostBuilder()
        .UseKestrel()
        .UseContentRoot(Directory.GetCurrentDirectory())
        .UseIISIntegration()
        .UseStartup<Startup>()
        .Build();

    host.Run();
}
```
Aplikacji ASP.NET Core tworzy serwer sieci web w jego głównej metody, konfigurowania i uruchamiania hosta za pośrednictwem wystąpienia [ `WebHostBuilder` ](/aspnet/core/fundamentals/hosting). Ten konstruktor zapewnia metody do Zezwalaj na hoście należy skonfigurować. W szablonie aplikacji są używane następujące konfiguracje:

* `UseKestrel`: Określa, że serwer Kestrel będzie używany przez aplikację
* `UseContentRoot(Directory.GetCurrentDirectory())`: Używa folder główny projektu sieci web jako główny zawartości aplikacji, gdy aplikacja została uruchomiona z tego folderu
* `.UseIISIntegration()`: Określa, czy aplikacja powinna współdziałać z usług IIS. Usługi IIS za pomocą platformy ASP.NET Core zarówno `UseKestrel` i `UseIISIntegration` muszą być określone.
* `.UseStartup<Startup>()`: Określa klasę uruchamiania.

  Kompilowanie i uruchamianie metody tworzenia IWebHost, który będzie hostować aplikację i uruchom ją nasłuchuje przychodzących żądań HTTP.

### <a name="startupcs"></a>Startup.cs

Klasa początkowa dla aplikacji jest określony w `UseStartup()` metody `WebHostBuilder`. Jest w tej klasie określą żądania obsługi potoku i konfigurowania usług.

Otwórz i sprawdź **Startup.cs** plik w projekcie:

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddConsole();

        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }

        app.Run(async (context) =>
        {
            await context.Response.WriteAsync("Hello World!");
        });
    }
}
```

Ta klasa uruchamiania zawsze muszą stosować się do następujących reguł:

 - Zawsze muszą być publiczne
 - Musi ona zawierać dwóch metod publicznych: `ConfigureServices` i `Configure`

`ConfigureServices` Metoda definiuje usług, które będą używane przez aplikację.

`Configure` Pozwala tworzyć swoje żądania potoku przy użyciu [oprogramowania pośredniczącego](/aspnet/core/fundamentals/middleware). Są to składniki używane w ramach potoku aplikacji ASP.NET do obsługi żądań i odpowiedzi. Potok HTTP składa się z liczbą delegatów żądania, wywoływana w sekwencji. Każdego delegata można obsłużyć żądania, samego lub przekazać je do następnej delegata.

Delegatów można skonfigurować za pomocą `Run`,`Map`, i `Use` metod `IApplicationBuilder`, ale `Run` metoda nigdy nie wywołują metody delegata dalej i zawsze należy używać na końcu potoku.

`Configure` Metoda wstępnie utworzonego szablonu został opracowany pod kątem wykonać kilka czynności. Po pierwsze konfiguruje obsługi strony do użycia podczas tworzenia wyjątków. Następnie wysyła odpowiedź do żądania strony sieci web za pomocą prostego "Hello World".

To proste Witaj, świecie projektu teraz uruchomić bez konieczności wprowadzania dodatkowego kodu dodawany. Aby uruchomić aplikację i wyświetlić je w przeglądarce, naciśnij przycisk odtwarzania (triangulacji) na pasku narzędzi:

![Uruchamianie aplikacji](media/asp-net-core-image5.png)

Program Visual Studio for Mac używa portu losowego, aby uruchomić projekt sieci web. Aby dowiedzieć się, co ten port jest, otwórz dane wyjściowe aplikacji, która znajduje się w obszarze **Widok > okienka**. Należy wyszukać dane wyjściowe podobne do przedstawionego poniżej:

![Wyświetlanie port nasłuchujący dane wyjściowe aplikacji](media/asp-net-core-image6.png)

Otwórz wybraną przeglądarkę i wprowadź `http://localhost:5000/`, zastępując `5000` z portem, który program Visual Studio wyniki w danych wyjściowych aplikacji. Powinien zostać wyświetlony tekst `Hello World!`:

![Przeglądarka wyświetlanie tekstu](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Dodawanie kontrolera

Aplikacje platformy ASP.NET Core Użyj wzorca projektowego Model-View-Controller (MVC), aby dostarczyć logiczne restrykcyjne rozdzielenie obowiązków dla poszczególnych części aplikacji. MVC składa się z następujących czynności:

- **Model**: Klasa, która odzwierciedla dane aplikacji.
- **Widok**: Wyświetla interfejs użytkownika aplikacji (jest to często danych modelu).
- **Kontroler**: Klasa, która obsługuje żądania przeglądarki reaguje na dane wejściowe użytkownika i interakcji.

Aby uzyskać więcej informacji na temat korzystania z platformy MVC dotyczą [omówienie platformy ASP.NET Core MVC](/aspnet/core/mvc/overview) przewodnik.

Aby dodać kontroler, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy nazwę projektu, a następnie wybierz pozycję **Dodaj > nowe pliki**. Wybierz **ogólne > pustą klasę**, a następnie wprowadź nazwę kontrolera:

    ![Okno dialogowe Nowy plik](media/asp-net-core-image8.png)

2. Nowy kontroler, Dodaj następujący kod:

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using System.Text.Encodings.Web;

    namespace Hello_ASP
    {
        public class HelloWorldController : Controller
        {
            //
            // GET: /HelloWorld/

            public string Index()
            {
                return "This is my default action...";
            }

        }
    }
    ```

3. Dodaj `Microsoft.AspNetCore.Mvc` zależności do projektu, klikając prawym przyciskiem myszy **zależności** folderu, a wybranie **Dodaj pakiet...** .

4. Użyj pola wyszukiwania, aby przejść do biblioteki NuGet programu `Microsoft.AspNetCore.Mvc`i wybierz **Dodaj pakiet**. Może to potrwać kilka minut, aby zainstalować i może pojawić się prośba o zaakceptowanie licencji różnych wymagane zależności:

    ![Dodaj pakiet Nuget](media/asp-net-core-image9.png)

5. W klasie uruchamiania, Usuń `app.Run` lambda i zestawu logiki routingu adresu URL używany przez MVC umożliwiający określenie, której kod: należy wywołać do następującego:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Upewnij się usunąć `app.Run` lambda, ponieważ spowoduje przesłonięcie logikę routingu.

    MVC posługuje się następującym formatem, aby określić, której kod wymagany do uruchomienia:

    `/[Controller]/[ActionName]/[Parameters]`

    Po dodaniu powyższym fragmencie kodu, informuje aplikację, aby domyślnie przyjmowało wartość `HelloWorld` kontrolera, a `Index` metody akcji.

6. Dodaj `services.AddMvc();` wywołanie `ConfigureServices` metody, jak przedstawiono poniżej:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    Można również przekazać informacje o parametrach z adresu URL do kontrolera.

7. Dodaj inną metodę do swojej HelloWorldController, jak przedstawiono poniżej:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Jeśli uruchomisz aplikację teraz, powinno zostać automatycznie otwarte przeglądarki:

    ![Uruchamianie aplikacji w przeglądarce](media/asp-net-core-image13.png)

9. Spróbuj przejść do `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` (zastępując `xxxx` za pomocą poprawnego portu), powinny pojawić się następujące:

    ![Uruchamianie aplikacji w przeglądarce z argumentami](media/asp-net-core-image10.png)


## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli zachodzi potrzeba Zainstaluj platformę .NET Core ręcznie na systemu Mac OS 10.11 (El Capitan) lub nowszym, wykonaj następujące czynności:

1. Przed rozpoczęciem instalacji platformy .NET Core, upewnij się, że wszystkie aktualizacje systemu operacyjnego zostały zaktualizowane do najnowszej stabilnej wersji. Można to sprawdzić, przechodząc do aplikacji App Store, a następnie wybierając kartę aktualizacje.

2. Wykonaj następujące kroki na [lokacji platformy .NET Core](https://www.microsoft.com/net/core#macos).

Upewnij się zakończyć wszystkie cztery kroki pomyślnie upewnij się, że pomyślnym zainstalowaniu platformy .NET Core.

## <a name="summary"></a>Podsumowanie

Ten przewodnik zapewniła wprowadzenie do platformy ASP.NET Core. Opisuje co to jest, kiedy należy używać i podano informacje na temat używania go w programie Visual Studio dla komputerów Mac.
Więcej informacji na temat następnych kroków w tym miejscu można znaleźć w następujących przewodnikach:
- [Platforma ASP.NET Core](/aspnet/core/?view=aspnetcore-2.1#build-web-ui-and-web-apis-using-aspnet-core-mvc) docs.
- [Tworzenie usług zaplecza dla natywnych aplikacji mobilnych](/aspnet/core/mobile/native-mobile-backend), który pokazuje, jak utworzyć usługę REST, za pomocą platformy ASP.NET Core dla aplikacji platformy Xamarin.Forms.
- [Praktyczne laboratorium platformy ASP.NET Core](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]