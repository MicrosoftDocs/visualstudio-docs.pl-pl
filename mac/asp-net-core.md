---
title: Wprowadzenie do korzystania z platformy ASP.NET Core
description: W tym artykule opisano, jak rozpocząć pracę z usługą ASP.NET w Visual Studio dla komputerów Mac, w tym instalację i tworzenie nowego projektu.
author: sayedihashimi
ms.author: sayedha
ms.date: 04/02/2019
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
no-loc:
- Blazor
- Blazor WebAssembly
ms.topic: how-to
ms.openlocfilehash: 7f8795b798b492370a08e55171c5627485c7869a
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584064"
---
# <a name="getting-started-with-aspnet-core"></a>Wprowadzenie do korzystania z platformy ASP.NET Core

 Visual Studio dla komputerów Mac ułatwia opracowywanie usługi aplikacji z obsługą najnowszej platformy deweloperskiej ASP.NET Core sieci Web. ASP.NET Core działa na platformie .NET Core, najnowszej ewolucji .NET Framework i środowiska uruchomieniowego. Jest on dostosowany do szybkiej wydajności, jest przeznaczony dla małych rozmiarów instalacji i zmieniany do uruchamiania w systemach Linux i macOS, a także w systemie Windows.

## <a name="installing-net-core"></a>Instalowanie programu .NET Core

Środowisko .NET Core 3,1 jest instalowane automatycznie podczas instalowania Visual Studio dla komputerów Mac. Aby uzyskać więcej informacji na temat wersji programu .NET Core obsługiwanych w Visual Studio dla komputerów Mac zobacz temat [Obsługa platformy .NET Core](./net-core-support.md).

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Tworzenie aplikacji ASP.NET Core w Visual Studio dla komputerów Mac

Otwórz Visual Studio dla komputerów Mac. Na ekranie startowym wybierz pozycję **Nowy projekt...**

![Okno dialogowe Nowy projekt](media/asp-net-core-2019-new-asp-core.png)

Spowoduje to wyświetlenie okna dialogowego Nowy projekt, w którym można wybrać szablon służący do tworzenia aplikacji.

Istnieje wiele projektów, które udostępniają wstępnie utworzony szablon, aby rozpocząć Kompilowanie aplikacji ASP.NET Core. Są to:

- **> pustej platformy .NET Core**
- **Interfejs API programu .NET Core >**
- **Aplikacja sieci Web platformy .NET Core >**
- **Aplikacja sieci Web platformy .NET Core > (Model-View-Controller)**
- **Aplikacja platformy .NET Core > Blazor Server**
- **Aplikacja .NET Core > Blazor WebAssembly**

![Opcje projektu ASP.NET](media/asp-net-core-2019-new-asp-core.png)

Wybierz **ASP.NET Core pustą aplikację sieci Web** i naciśnij przycisk **dalej**. Nadaj projektowi nazwę i naciśnij pozycję **Utwórz**. Spowoduje to utworzenie nowej aplikacji ASP.NET Core. W lewym okienku konsoli rozwiązania rozwiń drugą strzałkę, a następnie wybierz pozycję **Startup.cs**. Powinien wyglądać podobnie do poniższego obrazu:

![Nowy ASP.NET Core pusty widok projektu](media/asp-net-core-2019-empty-project.png)

ASP.NET Core pusty szablon tworzy aplikację sieci Web z dwoma domyślnymi plikami: **program.cs** i **Startup.cs**, które opisano poniżej. Tworzy również folder zależności, który zawiera zależności pakietu NuGet projektu, takie jak ASP.NET Core, .NET Core Framework i obiekty docelowe programu MSBuild, które kompilują projekt:

![okienko rozwiązania wyświetlania zależności](media/asp-net-core-2019-solution-dependencies.png)

### <a name="programcs"></a>Program.cs

Otwórz i sprawdź plik **program.cs** w projekcie. Zwróć uwagę, że w metodzie występuje kilka rzeczy `Main` — wpis do aplikacji:

```csharp
    public class Program
    {
        public static void Main(string[] args)
        {
            CreateWebHostBuilder(args).Build().Run();
        }

        public static IWebHostBuilder CreateWebHostBuilder(string[] args) =>
            WebHost.CreateDefaultBuilder(args)
                .UseStartup<Startup>();
    }
```

Aplikacja ASP.NET Core tworzy serwer sieci Web w swojej metodzie głównej przez skonfigurowanie i uruchomienie hosta za pomocą wystąpienia [`WebHostBuilder`](/aspnet/core/fundamentals/hosting) . Ten konstruktor udostępnia metody umożliwiające skonfigurowanie hosta. W aplikacji szablonu są używane następujące konfiguracje:

* `.UseStartup<Startup>()`: Określa klasę uruchomieniową.

Można jednak również dodać dodatkowe konfiguracje, takie jak:

* `UseKestrel`: Określa, że serwer Kestrel będzie używany przez aplikację
* `UseContentRoot(Directory.GetCurrentDirectory())`: Używa folderu głównego projektu sieci Web jako katalogu głównego zawartości aplikacji, gdy aplikacja zostanie uruchomiona z tego folderu
* `.UseIISIntegration()`: Określa, że aplikacja powinna współpracować z usługami IIS. Aby można było używać usług IIS z ASP.NET Coreami `UseKestrel` i `UseIISIntegration` należy je określić.

### <a name="startupcs"></a>Startup.cs

Klasa uruchamiania dla aplikacji jest określona w `UseStartup()` metodzie w `CreateWebHostBuilder` . W tej klasie należy określić potok obsługi żądań i skonfigurować usługi.

Otwórz i sprawdź plik **Startup.cs** w projekcie:

```csharp
    public class Startup
    {
        // This method gets called by the runtime. Use this method to add services to the container.
        // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
        public void ConfigureServices(IServiceCollection services)
        {
        }

        // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
        public void Configure(IApplicationBuilder app, IHostingEnvironment env)
        {
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

Ta klasa startowa musi zawsze być zgodna z następującymi regułami:

- Musi być zawsze publiczny
- Musi zawierać dwie metody publiczne: `ConfigureServices` i `Configure`

`ConfigureServices`Metoda definiuje usługi, które będą używane przez aplikację.

`Configure`Umożliwia tworzenie potoku żądania przy użyciu [oprogramowania pośredniczącego](/aspnet/core/fundamentals/middleware). Są to składniki używane w potoku aplikacji ASP.NET do obsługi żądań i odpowiedzi. Potok HTTP składa się z szeregu delegatów żądań wywoływanych w sekwencji. Każdy delegat może wybrać albo obsłużyć żądanie lub przekazać go do następnego delegata.

Można skonfigurować delegatów przy użyciu `Run` metod, `Map` , i `Use` w `IApplicationBuilder` , ale `Run` Metoda nigdy nie wywoła następnego delegata i zawsze powinna być używana na końcu potoku.

`Configure`Metoda wstępnie skompilowanego szablonu została skompilowana w celu wykonania kilku czynności. Najpierw konfiguruje stronę obsługi wyjątków do użycia podczas opracowywania. Następnie wysyła odpowiedź do strony żądającej sieci Web z prostym "Hello world".

Ta prosta Witaj, projekt światowy może działać teraz bez dodawania dodatkowego kodu. Aby uruchomić aplikację, możesz wybrać przeglądarkę, w której chcesz uruchomić aplikację, za pomocą listy rozwijanej po prawej stronie przycisku Odtwórz lub po prostu nacisnąć przycisk Odtwórz (trójkątny), aby użyć domyślnej przeglądarki:

![Uruchomienie przeglądarki](media/asp-net-web-picker.png)

Do uruchomienia projektu sieci Web Visual Studio dla komputerów Mac jest używany port losowy. Aby dowiedzieć się, jaki jest ten port, Otwórz dane wyjściowe aplikacji, która jest wyświetlana w obszarze **wyświetl > konsole**. Powinny znajdować się dane wyjściowe podobne do pokazanego poniżej:

![Dane wyjściowe aplikacji wyświetlające port nasłuchujący](media/asp-net-core-image6.png)

Po uruchomieniu projektu należy uruchomić domyślną przeglądarkę sieci Web, a następnie połączyć się z adresem URL wymienionym w danych wyjściowych aplikacji. Alternatywnie możesz otworzyć dowolną dowolnie wybraną przeglądarkę i wprowadzić `http://localhost:5000/` , zastępując ją `5000` portem, który program Visual Studio wyprowadza w danych wyjściowych aplikacji. Powinien zostać wyświetlony tekst `Hello World!` :

![tekst wyświetlany w przeglądarce](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Dodawanie kontrolera

Aplikacje ASP.NET Core korzystają ze wzorca projektowego Model-View-Controller (MVC), aby zapewnić logiczne Rozdzielenie obowiązków dla każdej części aplikacji. MVC składa się z następujących elementów:

- **Model**: Klasa, która reprezentuje dane aplikacji.
- **Widok**: wyświetla interfejs użytkownika aplikacji (który jest często danymi modelu).
- **Kontroler**: Klasa, która obsługuje żądania przeglądarki, reaguje na dane wejściowe i interakcje użytkownika.

Aby uzyskać więcej informacji na temat korzystania z MVC, zobacz Omówienie podręcznika [ASP.NET Core MVC](/aspnet/core/mvc/overview) .

Aby dodać kontroler, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy nazwę projektu i wybierz polecenie **dodaj > nowe pliki**. Wybierz pozycję **ogólne > pustą klasę**, a następnie wprowadź nazwę kontrolera:

    ![Okno dialogowe Nowy plik](media/asp-net-core-image8.png)

2. Dodaj następujący kod do nowego kontrolera:

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

3. Aby dodać `Microsoft.AspNetCore.Mvc` zależność do projektu, kliknij prawym przyciskiem myszy folder **zależności** i wybierz polecenie **Dodaj pakiet...**.

4. Użyj pola wyszukiwania, aby przejrzeć bibliotekę NuGet dla programu `Microsoft.AspNetCore.Mvc` , a następnie wybierz pozycję **Dodaj pakiet**. Instalacja może potrwać kilka minut, a użytkownik może zostać poproszony o zaakceptowanie różnych licencji dla wymaganych zależności:

    ![Dodaj NuGet](media/asp-net-core-image9.png)

5. W klasie startowej Usuń `app.Run` wyrażenie lambda i ustaw logikę routingu adresów URL używaną przez MVC do określenia, który kod powinien zostać wywołany w następujący sposób:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Upewnij się, że usunięto `app.Run` wyrażenie lambda, ponieważ spowoduje to zastąpienie logiki routingu.

    Aby określić kod do uruchomienia, MVC korzysta z następującego formatu:

    `/[Controller]/[ActionName]/[Parameters]`

    Po dodaniu powyższego fragmentu kodu zostanie wyszukana aplikacja domyślna dla `HelloWorld` kontrolera i `Index` Metoda działania.

6. Dodaj `services.AddMvc();` wywołanie do `ConfigureServices` metody, jak pokazano poniżej:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    Możesz również przekazać informacje o parametrach z adresu URL do kontrolera.

7. Dodaj kolejną metodę do HelloWorldController, jak pokazano poniżej:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Jeśli aplikacja zostanie uruchomiona teraz, powinna automatycznie otworzyć przeglądarkę:

    ![Uruchamianie aplikacji w przeglądarce](media/asp-net-core-image13.png)

9. Spróbuj przejść do `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` (zastępowanie `xxxx` prawidłowym portem), aby zobaczyć następujące elementy:

    ![Uruchamianie aplikacji w przeglądarce z argumentami](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli musisz ręcznie zainstalować platformę .NET Core na Mac OS 10,12 (Sierra) i wyższych, wykonaj następujące czynności:

1. Przed rozpoczęciem instalowania programu .NET Core upewnij się, że zaktualizowano wszystkie aktualizacje systemu operacyjnego do najnowszej stabilnej wersji. Możesz to sprawdzić, przechodząc do aplikacji ze sklepu App Store, a następnie wybierając kartę aktualizacje.

2. Wykonaj czynności opisane w [witrynie .NET Core](https://www.microsoft.com/net/core#macos).

Upewnij się, że wszystkie kroki zostały wykonane pomyślnie, aby upewnić się, że program .NET Core został pomyślnie zainstalowany.

## <a name="summary"></a>Podsumowanie

Ten przewodnik zawiera wprowadzenie do ASP.NET Core. Opisuje to, co to jest, kiedy należy z niego korzystać, i podano informacje dotyczące korzystania z niego w Visual Studio dla komputerów Mac.
Więcej informacji o następnych krokach można znaleźć w następujących przewodnikach:
- [ASP.NET Core](/aspnet/core/?view=aspnetcore-2.1) dokumentów.
- [Tworzenie usług zaplecza dla natywnych aplikacji mobilnych](/aspnet/core/mobile/native-mobile-backend), które pokazują, jak utworzyć usługę REST przy użyciu ASP.NET Core dla aplikacji platformy Xamarin. Forms.
- [ASP.NET Core laboratorium praktycznego](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]