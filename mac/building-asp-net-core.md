---
title: Tworzenie aplikacji ASP.NET Core
description: W tym artykule opisano, jak rozpocząć pracę z ASP.NET w programie Visual Studio dla komputerów Mac, w tym instalacji i tworzenia nowego projektu.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.openlocfilehash: 5600fd2f0b6d83a3bd27350a4d4f0137ea44ced2
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75398280"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Tworzenie aplikacji platformy ASP.NET Core w programie Visual Studio dla komputerów Mac

ASP.NET Core to platforma typu open source i wieloplatformowa do tworzenia nowoczesnych aplikacji połączonych z Internetem w chmurze, takich jak aplikacje i usługi internetowe, aplikacje IoT i zaplecze mobilne. ASP.NET aplikacje Core można uruchomić w [programie .NET Core](https://www.microsoft.com/net/core/platform) lub w środowiskach uruchomieniowych programu .NET Framework. Został zaprojektowany w celu zapewnienia zoptymalizowanej struktury programistycznej dla aplikacji, które są wdrażane w chmurze lub uruchamiane lokalnie. Składa się z komponentów modułowych przy minimalnym obciążeniu, dzięki czemu można zachować elastyczność podczas konstruowania rozwiązań. Aplikacje ASP.NET Core można tworzyć i uruchamiać na wielu platformach w systemach Windows, Mac i Linux. ASP.NET Core jest open source w [GitHub](https://github.com/aspnet/home).

W tym laboratorium utworzysz i eksplorujesz aplikację ASP.NET Core za pomocą programu Visual Studio dla komputerów Mac.

## <a name="objectives"></a>Cele

> [!div class="checklist"]
> * Tworzenie aplikacji internetowej ASP.NET Core
> * Poznaj ASP.NET model hostingu Core, konfiguracji i oprogramowania pośredniczącego
> * Debugowanie aplikacji sieci web ASP.NET Core

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio dla komputerów Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Docelowi odbiorcy

To laboratorium jest przeznaczone dla deweloperów, którzy są zaznajomieni z języka C#, chociaż głębokie doświadczenie nie jest wymagane.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Zadanie 1: Tworzenie nowej aplikacji ASP.NET Core

1. Uruchom **program Visual Studio dla komputerów Mac**.

2. Wybierz **opcję Plik > nowe rozwiązanie**.

3. Wybierz kategorię **aplikacji .NET Core >** i szablon ASP.NET Core Web App **(C#).** Kliknij przycisk **alej**.

    ![](media/netcore-image1.png)

4. Wprowadź nazwę **"CoreLab"** i kliknij przycisk **Utwórz,** aby utworzyć projekt. To zajmie chwilę, aby zakończyć.

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Zadanie 2: Zwiedzanie rozwiązania

1. Domyślny szablon spowoduje powstanie rozwiązania z jednym projektem ASP.NET Core o nazwie **CoreLab**. Rozwiń węzeł projektu, aby udostępnić jego zawartość.

    ![](media/netcore-image3.png)

2. Ten projekt jest zgodny z paradygmatem kontrolera widoku modelu (MVC), aby zapewnić wyraźny podział obowiązków między danymi (modele), prezentacją (widokami) i funkcjami (kontrolerami). Otwórz plik **HomeController.cs** z folderu **Kontrolery.**

    ![](media/netcore-image4.png)

3. **HomeController** klasy po konwencji obsługuje wszystkie przychodzące żądania, które zaczynają się **od /Home**. Metoda **Indeks** obsługuje żądania do katalogu głównego katalogu `http://site.com/Home`(np. ) i inne metody obsługi żądań do ich `http://site.com/Home/About`nazwanej ścieżki na podstawie konwencji, takich jak **About()** obsługi żądań do . Oczywiście, to wszystko jest konfigurowalne. Jedną z godnych uwagi jest to, że **HomeController** jest domyślnym kontrolerem w nowym projekcie, więc żądania do katalogu głównego witryny`http://site.com`( ) przechodziłyby przez **Index()** **HomeController,** podobnie jak żądania do `http://site.com/Home` lub `http://site.com/Home/Index`.

    ![](media/netcore-image5.png)

4. Projekt ma również **folder Widoki,** który zawiera inne foldery, które są mapowane do każdego kontrolera (a także jeden dla widoków **udostępnionych.** Na przykład plik CSHTML widoku (rozszerzenie HTML) dla **/Home/About** ścieżka będzie w **views/Home/About.cshtml**. Otwórz ten plik.

    ![](media/netcore-image6.png)

5. Ten plik CSHTML używa składni Razor do renderowania HTML na podstawie kombinacji standardowych tagów i wbudowanego języka C#. Więcej informacji na ten temat można znaleźć w [dokumentacji online.](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c)

    ![](media/netcore-image7.png)

6. Rozwiązanie zawiera również folder **wwwroot,** który będzie głównym źródłem witryny sieci Web. Statyczną zawartość witryny, taką jak CSS, obrazy i biblioteki JavaScript, można umieścić bezpośrednio przy ścieżkach, na których mają się znajdować podczas wdrażania witryny.

    ![](media/netcore-image8.png)

7. Istnieje również wiele plików konfiguracyjnych, które służą do zarządzania projektem, jego pakiety i aplikacji w czasie wykonywania. Na przykład domyślna [konfiguracja](/aspnet/core/fundamentals/configuration) aplikacji jest przechowywana w **pliku appsettings.json**. Zagnieżdżone poniżej pliku appsettings.json jest **appsettings. Development.json.** W tym miejscu można zastąpić niektóre/wszystkie te ustawienia na podstawie środowiska. Visual Studio dla komputerów Mac będzie zagnieżdżać pliki w ten sposób przy użyciu tej samej logiki co Visual Studio dla systemu Windows, dzięki czemu pliki, które należy uzyskać dostęp częściej są w czołówce. 

    ![](media/netcore-build-nested.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Zadanie 3: Opis sposobu hosta aplikacji

1. Z **Eksploratora rozwiązań**otwórz **Program.cs**. Jest to program inichura, który uruchomi aplikację.

    ![](media/netcore-image10.png)

2. Chociaż istnieją tylko dwa wiersze kodu w tym miejscu, są one istotne. Rozbijmy je. Najpierw tworzony jest nowy **WebHostBuilder.** ASP.NET aplikacje Core wymagają hosta, w którym mają być wykonywane. Host musi implementować interfejs **IWebHost,** który udostępnia kolekcje funkcji i usług oraz metodę **Start.** Host jest zazwyczaj tworzony przy użyciu wystąpienia **WebHostBuilder**, który tworzy i zwraca **WebHost** wystąpienie. **WebHost** odwołuje się do serwera, który będzie obsługiwać żądania.

    ![](media/netcore-image11.png)

3. Podczas **gdy WebHostBuilder** jest odpowiedzialny za tworzenie hosta, który będzie bootstrap serwera dla aplikacji, wymaga zapewnienia serwera, który implementuje **IServer**. Domyślnie jest to **[Kestrel](/aspnet/core/fundamentals/servers/kestrel)**, wieloplatformowy serwer www dla ASP.NET Core oparty na **libuv**, który jest międzyplatformową asynchronicznymi bibliotekami we/wy.

    ![](media/netcore-image12.png)

4. Następnie jest ustawiony katalog główny zawartości serwera. Określa, gdzie wyszukuje pliki zawartości, takie jak pliki MVC View. Domyślnym katalogiem głównym zawartości jest folder, z którego jest uruchamiana aplikacja.

    ![](media/netcore-image13.png)

5. Jeśli aplikacja musi współpracować z serwerem sieci web internetowych internetowych internetowych usług informacyjnych (IIS), metoda **UseIISIntegration** powinna być wywoływana jako część tworzenia hosta. Że to nie konfiguruje serwera, jak **UseKestrel** nie. Aby używać programów IIS z ASP.NET Core, należy określić zarówno **usekestrel,** jak i **useiisintegration**. **Pustułka** jest przeznaczona do uruchamiania za serwerem proxy i nie powinna być wdrażana bezpośrednio w internecie. **UseIISIntegration** określa usługi IIS jako serwer odwrotnego serwera proxy, ale jest to istotne tylko w przypadku uruchamiania na komputerach z usługami IIS. Jeśli wdrożysz aplikację w systemie Windows, pozostaw ją w. Inaczej nie boli.

    ![](media/netcore-image14.png)

6. Jest to czystsza praktyka, aby oddzielić ładowanie ustawień od boottrapping aplikacji. Aby łatwo to zrobić, **UseStartup** jest wywoływana, aby określić, że **startup** klasy ma być wywoływana dla ładowania ustawień i innych zadań uruchamiania, takich jak wstawianie oprogramowania pośredniczącego do potoku HTTP. Może być wiele **UseStartup** wywołania z oczekiwaniem, że każdy z nich zastępuje poprzednie ustawienia w razie potrzeby.

    ![](media/netcore-image15.png)

7. Ostatnim krokiem w tworzeniu **IWebHost** jest **wywołanie Build**.

    ![](media/netcore-image16.png)

8. Podczas **IWebHost** klasy są wymagane do zaimplementowania **start**nieblokujący , ASP.NET Podstawowe projekty mają metodę rozszerzenia o nazwie **Uruchom,** która zawija **Start** z kodem blokowania, więc nie trzeba ręcznie zapobiec metody zamykania natychmiast.

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Zadanie 4: Uruchamianie i debugowanie aplikacji

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu **CoreLab** i wybierz polecenie **Opcje**.

    ![](media/netcore-image18.png)

2. Okno dialogowe **Opcje projektu** zawiera wszystko, czego potrzebujesz, aby dostosować sposób tworzenia i uruchamiania aplikacji. Wybierz węzeł **Uruchom > > węzeł Domyślny** z lewego panelu.

3. Zaznacz **pole wyboru Uruchom na konsoli zewnętrznej** i wyewidencjonuj pozycję **Wstrzymaj wyjście konsoli**. Zwykle aplikacja hostowana samodzielnie nie będzie widoczna w swojej konsoli, ale zamiast tego rejestrowałaby swoje wyniki na konsoli **wyjściowej.** Na potrzeby tego laboratorium pokażemy go również w osobnym oknie, chociaż nie musisz tego robić podczas normalnego rozwoju.

4. Kliknij przycisk **OK**.

    ![](media/netcore-image19.png)

5. Naciśnij **klawisz F5,** aby utworzyć i uruchomić aplikację. Alternatywnie można wybrać **uruchom > rozpocznij debugowanie**.

6. Program Visual Studio dla komputerów Mac uruchomi dwa okna. Pierwszym z nich jest okno konsoli, które zapewnia widok do aplikacji serwera hostowanego samodzielnie.

    ![](media/netcore-image20.png)

7. Drugi to typowe okno przeglądarki do testowania witryny. O ile przeglądarka wie, ta aplikacja może być hostowana w dowolnym miejscu. Kliknij przycisk **Informacje,** aby przejść do tej strony.

    ![](media/netcore-image21.png)

8. Między innymi strona about renderuje niektóre tekst ustawiony w kontrolerze.

    ![](media/netcore-image22.png)

9. Zachowaj otwarte okna i wróć do programu Visual Studio dla komputerów Mac. Otwórz **kontrolery/HomeController.cs,** jeśli nie jest jeszcze otwarty.

    ![](media/netcore-image23.png)

10. Ustaw punkt przerwania w pierwszym wierszu **O** metody. Można to zrobić, klikając na margines lub ustawiając kursor na wierszu i naciskając **klawisz F9**. Ten wiersz ustawia niektóre dane w kolekcji **ViewData** renderowane na stronie CSHTML w **widoku/Strona główna/Informacje.cshtml**.

    ![](media/netcore-image24.png)

11. Wróć do przeglądarki i odśwież stronę informacje. Spowoduje to wyzwolenie punktu przerwania w programie Visual Studio dla komputerów Mac.

12. Najedź myszką na **element członkowski ViewData,** aby wyświetlić jego dane. Można również rozwinąć jego elementy podrzędne, aby wyświetlić zagnieżdżone dane.

    ![](media/netcore-image25.png)

13. Usuń punkt przerwania aplikacji przy użyciu tej samej metody, która została użyta do dodania.

14. **Otwórz widoki/Strona główna/Informacje.cshtml**.

15. Zmień tekst **"dodatkowy"** na **"zmieniony"** i zapisz plik.

    ![](media/netcore-image26.png)

16. Naciśnij przycisk **Kontynuuj,** aby kontynuować wykonywanie.

    ![](media/netcore-image27.png)

17. Wróć do okna przeglądarki, aby wyświetlić zaktualizowany tekst. Ta zmiana może być wykonana w dowolnym momencie i nie musi wymagać punktu przerwania debugera. Odśwież przeglądarkę, jeśli nie widzisz od razu odzwierciedlonej zmiany.

    ![](media/netcore-image28.png)

18. Zamknij okno przeglądarki testowej i konsolę aplikacji. Spowoduje to zatrzymanie debugowania, jak również.

## <a name="task-5-application-startup-configuration"></a>Zadanie 5: Konfiguracja uruchamiania aplikacji

1. Z **Eksploratora rozwiązań**otwórz **Startup.cs**. Można zauważyć, niektóre czerwone squiggles początkowo jako pakiety NuGet są przywracane w tle i kompilator Roslyn tworzy pełny obraz zależności projektu.

    ![](media/netcore-image29.png)

2. Znajdź **metodę Uruchamianie.** Ta sekcja definiuje początkową konfigurację aplikacji i jest gęsto zapakowana. Rozbijmy to.

    ![](media/netcore-image30.png)

3. Metoda rozpoczyna się od zainicjowania **ConfigurationBuilder** i ustawienie jego ścieżki podstawowej.

    ![](media/netcore-image31.png)

4. Następnie ładuje wymagany plik **appsettings.json.**

    ![](media/netcore-image32.png)

5. Następnie próbuje załadować plik **appsettings.json** specyficzny dla środowiska, który zastąpi istniejące ustawienia. Na przykład jest to dostarczone **appsettings. Development.json** plik używany dla tego określonego środowiska. Aby dowiedzieć się więcej o konfiguracji w ASP.NET Core, zapoznaj się z [docs](/aspnet/core/fundamentals/configuration).

    ![](media/netcore-image34.png)

6. Na koniec zmienne środowiskowe są dodawane do konstruktora konfiguracji, a konfiguracja jest komptuje i ustawiana do użycia.

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Zadanie 6: Wstawianie oprogramowania pośredniczącego aplikacji

1. Znajdź **Configure** metody w **startup** klasy. W tym miejscu skonfigurowano wszystkie oprogramowanie pośredniczące, dzięki czemu można je wstawić do potoku HTTP i użyć do przetworzenia każdego żądania na serwerze. Chociaż ta metoda jest wywoływana tylko raz, zawartość metod (takich jak **UseStaticFiles)** mogą być wykonywane na każde żądanie.

    ![](media/netcore-image36.png)

2. Można również dodać dodatkowe oprogramowanie pośredniczące do wykonania w ramach potoku. Dodaj poniższy kod po **aplikacji. UseStaticFiles** automatycznie dodać nagłówek **X-Test** do każdej odpowiedzi wychodzącej. IntelliSense pomoże wypełnić kod podczas pisania.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Naciśnij **klawisz F5,** aby zbudować i uruchomić projekt.

4. Możemy użyć przeglądarki, aby sprawdzić nagłówki, aby sprawdzić, czy są dodawane. Poniższe instrukcje są dla Safari, ale możesz zrobić to samo w [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) lub [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console).

5. Po załadowaniu witryny przez przeglądarkę wybierz pozycję **Safari > Preferences**.

6. Na karcie **Zaawansowane** zaznacz **menu Pokaż tworzenie na pasku menu** i zamknij okno dialogowe.

    ![](media/netcore-image37.png)

7. Wybierz **pozycję Rozwijaj > Pokaż zasoby strony**.

8. Odśwież okno przeglądarki, aby nowo otwarte narzędzia programistyczne mogły śledzić i analizować ruch i zawartość.

9. Strona HTML hosta lokalnego renderowana przez serwer będzie elementem wybranym domyślnie.

    ![](media/netcore-image38.png)

10. Rozwiń **pasek boczny Szczegóły**.

    ![](media/netcore-image39.png)

11. Przewiń do dołu paska bocznego, aby zobaczyć nagłówek odpowiedzi dodany w kodzie wcześniej.

    ![](media/netcore-image40.png)

12. Zamknij okno przeglądarki i konsolę, gdy jest spełniona.

## <a name="summary"></a>Podsumowanie

W tym laboratorium dowiesz się, jak rozpocząć tworzenie aplikacji ASP.NET Core za pomocą programu Visual Studio dla komputerów Mac. Jeśli chcesz eksplorować tworzenie aplikacji bazy danych filmów bardziej kompletne, zobacz Wprowadzenie do [ASP.NET Core MVC](/aspnet/core/tutorials/first-mvc-app/start-mvc) samouczek.
