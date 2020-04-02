---
title: Wprowadzenie do korzystania z platformy ASP.NET Core
description: W tym artykule opisano, jak rozpocząć pracę z ASP.NET w programie Visual Studio dla komputerów Mac, w tym instalacji i tworzenia nowego projektu.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/13/2017
ms.assetid: 6E8B0C90-33D6-4546-8207-CE0787584565
ms.custom: video
ms.openlocfilehash: 5f1a617c5562c4f95fec94ae449f48b681fcb7ef
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543757"
---
# <a name="getting-started-with-aspnet-core"></a>Wprowadzenie do korzystania z platformy ASP.NET Core

 Program Visual Studio dla komputerów Mac ułatwia tworzenie usługi aplikacji dzięki obsłudze najnowszej platformy programistycznej ASP.NET Core Web. ASP.NET Core działa na .NET Core, najnowszej ewolucji programu .NET Framework i środowiska wykonawczego. Został dostrojony pod kątem szybkiej wydajności, uwzględniony pod kątem małych rozmiarów instalacji i ponownie wyobrażony, aby działać na Linuksie i macOS, a także w systemie Windows.

## <a name="installing-net-core"></a>Instalowanie programu .NET Core

Program .NET Core 1.1 jest instalowany automatycznie podczas instalowania programu Visual Studio dla komputerów Mac.

## <a name="creating-an-aspnet-core-app-in-visual-studio-for-mac"></a>Tworzenie aplikacji ASP.NET Core w programie Visual Studio dla komputerów Mac

Otwórz program Visual Studio dla komputerów Mac. Na stronie powitalnej wybierz **pozycję Nowy projekt...**

![Okno dialogowe Nowy projekt](media/asp-net-core-image1.png)

Spowoduje to wyświetlenie okna dialogowego Nowy projekt, co umożliwi wybranie szablonu do utworzenia aplikacji.

Istnieje wiele projektów, które zapewnią Ci wstępnie utworzony szablon, aby rozpocząć tworzenie ASP.NET podstawowej aplikacji. Są to:

- **> rdzenia .NET ASP.NET rdzenia pustej aplikacji sieci Web**
- **> core ASP.NET core .NET**
- **Interfejs API sieci Web > core ASP.NET net**
- **Wieloplatformowa aplikacja > > połączoną aplikacją**

![ASP.NET opcje projektu](media/asp-net-core-image11.png)

Wybierz **ASP.NET Core Empty Web Application** i naciśnij przycisk **Dalej**. Nadaj projektowi nazwę i naciśnij klawisz **Utwórz**. Spowoduje to utworzenie nowej aplikacji ASP.NET Core, która powinna wyglądać podobnie do poniższego obrazu:

![Nowy widok pustego projektu ASP.NET core](media/asp-net-core-image4.png)

ASP.NET Core Empty Web Application tworzy aplikację internetową z dwoma plikami domyślnymi: **Program.cs** i **Startup.cs**, które zostały wyjaśnione poniżej. Tworzy również folder zależności, który zawiera zależności pakietu NuGet projektu, takie jak ASP.NET Core, .NET Core framework i MSBuild obiektów docelowych, które tworzą projekt:

![Klawiatura rozdzielająca z zależnościami](media/asp-net-core-image12.png)

### <a name="programcs"></a>Program.cs

Otwórz i sprawdź **plik Program.cs** w projekcie. Należy zauważyć, że dwie `Main` rzeczy dzieją się w metodzie — wpis do aplikacji:

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

Aplikacja ASP.NET Core tworzy serwer www w swojej głównej metodzie, konfigurując [`WebHostBuilder`](/aspnet/core/fundamentals/hosting)i uruchamiając hosta za pośrednictwem wystąpienia . Ten konstruktor udostępnia metody umożliwiające konfigurację hosta. W aplikacji szablonu używane są następujące konfiguracje:

* `UseKestrel`: Określa, że serwer Kestrel będzie używany przez aplikację
* `UseContentRoot(Directory.GetCurrentDirectory())`: Używa folderu głównego projektu internetowego jako katalogu głównego zawartości aplikacji po uruchomieniu aplikacji z tego folderu
* `.UseIISIntegration()`: Określa, że aplikacja powinna współpracować z iis. Aby używać IIS z ASP.NET `UseKestrel` `UseIISIntegration` Core zarówno i muszą być określone.
* `.UseStartup<Startup>()`: Określa klasę Uruchamiani.

  Build and Run metody kompilacji IWebHost, który będzie hostować aplikację i uruchomić go nasłuchiwania przychodzących żądań HTTP.

### <a name="startupcs"></a>Startup.cs

Startup Klasy dla aplikacji jest `UseStartup()` określony w `WebHostBuilder`metodzie na . Jest w tej klasie, która określi potok obsługi żądań i gdzie można skonfigurować żadnych usług.

Otwórz i sprawdź plik **Startup.cs** w projekcie:

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

Ta klasa uruchamiania musi zawsze przestrzegać następujących reguł:

- Musi być zawsze publiczna
- Musi zawierać dwie metody `ConfigureServices` publiczne:`Configure`

Metoda `ConfigureServices` definiuje usługi, które będą używane przez aplikację.

Umożliwia `Configure` skomponowanie potoku żądania przy użyciu [oprogramowania pośredniczącego](/aspnet/core/fundamentals/middleware). Są to składniki używane w ASP.NET potoku aplikacji do obsługi żądań i odpowiedzi. Potok HTTP składa się z wielu delegatów żądania, wywoływanych w kolejności. Każdy pełnomocnik może wybrać do obsługi samego żądania lub przekazać go do następnego pełnomocnika.

Delegatów można skonfigurować przy `Run``Map`użyciu `Use` , `IApplicationBuilder`i metody `Run` na , ale metoda nigdy nie wywoła następnego delegata i zawsze powinny być używane na końcu potoku.

Metoda `Configure` wstępnie utworzonego szablonu jest zbudowana, aby zrobić kilka rzeczy. Najpierw konfiguruje stronę obsługi wyjątków do użycia podczas tworzenia. Następnie wysyła odpowiedź na stronę internetową z prośbą z prostym "Hello World".

Ten prosty projekt Hello, World można uruchomić teraz bez dodatkowego kodu są dodawane. Aby uruchomić aplikację i wyświetlić ją w przeglądarce, naciśnij przycisk Odtwórz (trójkątny) na pasku narzędzi:

![Uruchamianie aplikacji](media/asp-net-core-image5.png)

Program Visual Studio dla komputerów Mac używa losowego portu do uruchomienia projektu sieci web. Aby dowiedzieć się, jaki to port, otwórz dane wyjściowe aplikacji, które jest wymienione w obszarze **Wyświetl > Klocki**. Powinieneś znaleźć dane wyjściowe podobne do pokazanego poniżej:

![Wyjście aplikacji wyświetlające port nasłuchujący](media/asp-net-core-image6.png)

Otwórz przeglądarkę wyboru i `http://localhost:5000/`wprowadź `5000` , zastępując port, który visual studio danych wyjściowych w danych wyjściowych aplikacji. Powinien zostać wyświetlony `Hello World!`tekst:

![przeglądarka z tekstem](media/asp-net-core-image7.png)

## <a name="adding-a-controller"></a>Dodawanie kontrolera

ASP.NET podstawowych aplikacji używać wzorca projektu model-view-controller (MVC), aby zapewnić logiczne oddzielenie obowiązków dla każdej części aplikacji. MVC składa się z następujących elementów:

- **Model:** Klasa reprezentująca dane aplikacji.
- **Widok**: Wyświetla interfejs użytkownika aplikacji (który jest często dane modelu).
- **Controller**: Klasa, która obsługuje żądania przeglądarki, odpowiada na dane wejściowe i interakcji użytkownika.

Aby uzyskać więcej informacji na temat korzystania z MVC, zapoznaj się [z omówieniem ASP.NET Przewodnik Core MVC.](/aspnet/core/mvc/overview)

Aby dodać kontroler, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy nazwę projektu i wybierz pozycję **Dodaj > nowe pliki**. Wybierz **opcję > klasa pusta**i wprowadź nazwę kontrolera:

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

3. Dodaj `Microsoft.AspNetCore.Mvc` zależność do projektu, klikając prawym przyciskiem myszy folder **Zależności** i wybierając pozycję **Dodaj pakiet...**.

4. Użyj pola Wyszukiwania, aby przeglądać `Microsoft.AspNetCore.Mvc`bibliotekę NuGet dla programu , a następnie wybierz pozycję **Dodaj pakiet**. Może to potrwać kilka minut, aby zainstalować i może być monit o zaakceptowanie różnych licencji dla wymaganych zależności:

    ![Dodaj Nuget](media/asp-net-core-image9.png)

5. W startup klasy usuń `app.Run` lambda i ustawić logikę routingu adresów URL używane przez MVC, aby określić, który kod należy wywołać na następujące:

    ```csharp
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=HelloWorld}/{action=Index}/{id?}");
    });
    ```

    Upewnij się, `app.Run` aby usunąć lambda, ponieważ spowoduje to zastąpienie logiki routingu.

    MVC używa następującego formatu, aby określić, który kod ma być uruchamiany:

    `/[Controller]/[ActionName]/[Parameters]`

    Po dodaniu fragmentu kodu powyżej, informujesz aplikację, aby `HelloWorld` domyślnie `Index` do kontrolera i metody akcji.

6. Dodaj `services.AddMvc();` wywołanie `ConfigureServices` metody, jak pokazano poniżej:

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
    }
    ```

    Można również przekazać informacje o parametrach z adresu URL do kontrolera.

7. Dodaj inną metodę do HelloWorldController, jak pokazano poniżej:

    ```csharp
    public string Xamarin(string name)
    {
        return HtmlEncoder.Default.Encode($"Hello {name}, welcome to Visual Studio for Mac");
    }
    ```

8. Jeśli uruchomisz aplikację teraz, powinna ona automatycznie otworzyć przeglądarkę:

    ![Uruchamianie aplikacji w przeglądarce](media/asp-net-core-image13.png)

9. Spróbuj przejść do `http://localhost:xxxx/HelloWorld/Xamarin?name=Amy` (zastępując `xxxx` właściwym portem), powinieneś zobaczyć następujące elementy:

    ![Uruchamianie aplikacji w przeglądarce z argumentami](media/asp-net-core-image10.png)

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Jeśli chcesz ręcznie zainstalować program .NET Core w systemie Mac OS 10.11 (El Capitan) lub nowszym, wykonaj następujące czynności:

1. Przed rozpoczęciem instalowania programu .NET Core upewnij się, że wszystkie aktualizacje systemu operacyjnego zostały zaktualizowane do najnowszej stabilnej wersji. Możesz to sprawdzić, przechodząc do aplikacji App Store i wybierając kartę Aktualizacje.

2. Wykonaj kroki wymienione w [witrynie .NET Core](https://www.microsoft.com/net/core#macos).

Upewnij się, że wszystkie cztery kroki zostały pomyślnie ukończone, aby upewnić się, że program .NET Core został pomyślnie zainstalowany.

## <a name="summary"></a>Podsumowanie

Ten przewodnik dał wprowadzenie do ASP.NET Core. Opisano w nim, co to jest, kiedy go używać i podano informacje dotyczące używania go w programie Visual Studio dla komputerów Mac.
Aby uzyskać więcej informacji na temat kolejnych kroków w tym miejscu, zapoznaj się z następującymi przewodnikami:
- ASP.NET dokumenty [Core.](/aspnet/core/)
- [Tworzenie usług wewnętrznej bazy danych dla natywnych aplikacji mobilnych,](/aspnet/core/mobile/native-mobile-backend)który pokazuje, jak utworzyć usługę REST przy użyciu ASP.NET Core dla aplikacji Xamarin.Forms.
- [ASP.NET Core praktyczne laboratorium](https://github.com/Microsoft/vs4mac-labs/tree/master/Web/Getting-Started).

## <a name="related-video"></a>Podobne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Build-Your-First-App/player]