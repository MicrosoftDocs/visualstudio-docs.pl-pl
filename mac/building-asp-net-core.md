---
title: Tworzenie aplikacji w programie Visual Studio dla komputerów Mac programu ASP.NET Core
description: W tym artykule opisano sposób rozpoczęcia pracy z programem ASP.NET w programie Visual Studio dla komputerów Mac, w tym instalacji i tworzenia nowego projektu.
author: sayedihashimi
ms.author: sayedha
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.openlocfilehash: f0a2e8433877b3eb61228a886280707f3b4a37fe
ms.sourcegitcommit: 7fbfb2a1d43ce72545096c635df2b04496b0be71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67693143"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Tworzenie aplikacji w programie Visual Studio dla komputerów Mac programu ASP.NET Core 

Platforma ASP.NET Core to architektura typu open source i dla wielu platform służąca do tworzenia nowoczesnych oparte na chmurze aplikacji połączonych z Internetem, takich jak aplikacje sieci web i usług, aplikacji IoT oraz zapleczy aplikacji mobilnych. Aplikacje platformy ASP.NET Core mogą być uruchamiane [platformy .NET Core](https://www.microsoft.com/net/core/platform) lub środowiska uruchomieniowego .NET Framework. Została zaprojektowana do zapewnienia architektura deweloperska zoptymalizowane aplikacje, które są wdrażane w chmurze lub lokalnie. Składa się z modułowej składniki przy minimalnym obciążeniu, więc Zachowaj elastyczność podczas konstruowania rozwiązania. Można tworzyć i uruchamiać aplikacje dla wielu platform ASP.NET Core na Windows, Mac i Linux. Platforma ASP.NET Core to "open source" na [GitHub](https://github.com/aspnet/home).

W tym laboratorium należy utworzyć i eksplorowanie aplikacji ASP.NET Core z programem Visual Studio dla komputerów Mac.

## <a name="objectives"></a>Cele

> [!div class="checklist"]
> * Tworzenie aplikacji internetowej platformy ASP.NET Core
> * Zapoznaj się z platformy ASP.NET Core hostingu, konfiguracji i oprogramowanie pośredniczące modelu
> * Debugowanie aplikacji sieci web ASP.NET Core

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Odbiorców

W tym laboratorium jest przeznaczona dla deweloperów, którzy są zaznajomieni z C#, ale doświadczenie nie jest wymagana.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Zadanie 1. Tworzenie nowej aplikacji platformy ASP.NET Core

1. Uruchom **programu Visual Studio dla komputerów Mac**.

2. Wybierz **Plik > nowe rozwiązanie**.

3. Wybierz **platformy .NET Core > App** kategorii i **aplikację sieci Web platformy ASP.NET Core (C#)** szablonu. Kliknij przycisk **Dalej**.

    ![](media/netcore-image1.png)

4. Wprowadź nazwę **"CoreLab"** i kliknij przycisk **Utwórz** do tworzenia projektu. Potrwa kilka minut, aby zakończyć.

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Zadanie 2. Podróżujący rozwiązania

1. Domyślny szablon generuje rozwiązanie z jednym projektem platformy ASP.NET Core o nazwie **CoreLab**. Rozwiń węzeł projektu, aby udostępnić jego zawartość.

    ![](media/netcore-image3.png)

2. Ten projekt jest zgodna paradygmat model-view-controller (MVC), zapewnienie wyraźny podział obowiązków między danych (modeli), prezentacji (widoki) i funkcje (kontrolery). Otwórz **HomeController.cs** plik wchodzącej w skład **kontrolerów** folderu.

    ![](media/netcore-image4.png)

3. **HomeController** klasy przez Konwencję — obsługuje wszystkie żądania przychodzące, które zaczyna się **/Home**. **Indeksu** obsługiwała żądania do głównego katalogu (takich jak `http://site.com/Home`) i innych metod obsługi żądań do swojej ścieżki o nazwie oparte na Konwencji, takich jak **About()** obsługiwanie żądań `http://site.com/Home/About`. Oczywiście jest to wszystkie konfigurowalne. Co warto jest fakt, że **HomeController** jest domyślny kontroler w nowym projekcie, dlatego żądania do katalogu głównego witryny (`http://site.com`) przechodził **indeks()** z  **HomeController** podobnie jak w przypadku żądań `http://site.com/Home` lub `http://site.com/Home/Index`.

    ![](media/netcore-image5.png)

4. Projekt ma również **widoków** folder, który zawiera inne foldery, które mapowania na każdy kontroler (oraz jeden dla **Shared** widoków. Na przykład, Wyświetl plik CSHTML (rozszerzenie HTML) do **/Home/About** byłaby to ścieżka w **Views/Home/About.cshtml**. Otwórz ten plik.

    ![](media/netcore-image6.png)

5. Ten plik CSHTML używa składni Razor do renderowania elementów HTML oparte na kombinacji standardowych tagów i wbudowany języka C#. Dowiedz się więcej o tym w [dokumentacji online](https://docs.microsoft.com/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

    ![](media/netcore-image7.png)

6. Rozwiązanie zawiera także **wwwroot** folder, który będzie katalog główny witryny sieci web. Możesz umieścić zawartości statycznej witryny, takiej jak CSS, obrazów i bibliotek JavaScript bezpośrednio w ścieżkach, o których mają one miały po wdrożeniu witryny.

    ![](media/netcore-image8.png)

7. Dostępne są także różne pliki konfiguracji, które służą do zarządzania projektu, jego pakietów i aplikacji w czasie wykonywania. Na przykład, domyślna aplikacja [konfiguracji](https://docs.microsoft.com/aspnet/core/fundamentals/configuration) są przechowywane w **appsettings.json**. Jednak można zastąpić niektórych lub wszystkich tych ustawień na podstawie na środowisku, takie jak, zapewniając **appsettings. Development.JSON** plik **rozwoju** środowiska.

    ![](media/netcore-image9.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Zadanie 3. Zrozumienie, jak aplikacja jest obsługiwana

1. Z **Eksploratora rozwiązań**, otwórz **Program.cs**. Jest to program inicjujący, który uruchomi aplikację.

    ![](media/netcore-image10.png)

2. Gdy istnieją tylko dwa wiersze kodu w tym miejscu, są one istotne. Możemy podzielić je. Po pierwsze, nowy **WebHostBuilder** zostanie utworzony. Aplikacje platformy ASP.NET Core wymagają hosta, w której chcesz wykonać. Host musi implementować **IWebHost** interfejs, który udostępnia kolekcje funkcji i usług, a **Start** metody. Host jest zwykle tworzony przy użyciu wystąpienia **WebHostBuilder**, który tworzy i zwraca **WebHost** wystąpienia. **WebHost** odwołuje się do serwera, który będzie obsługiwać żądania.

    ![](media/netcore-image11.png)

3. Gdy **WebHostBuilder** odpowiada dla tworzenia hosta, który spowoduje uruchomienie serwera aplikacji, wymaga zapewnienia serwera, który implementuje **IServer**. Domyślnie jest to  **[Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)** , na podstawie serwera sieci web dla wielu platform dla platformy ASP.NET Core **libuv**, czyli bibliotekę asynchronicznych operacji We/Wy dla wielu platform.

    ![](media/netcore-image12.png)

4. Następnie serwera głównego zawartości jest ustawiony. Określa, gdzie wyszukiwania dla plików zawartości, takich jak pliki widoku składnika MVC. Domyślny katalog główny zawartości jest folder, w którym aplikacja jest uruchomiona.

    ![](media/netcore-image13.png)

5. Jeśli aplikacja musi działać z serwerem sieci web usług Internet Information Services (IIS), **UseIISIntegration** metoda powinna być wywoływana w ramach tworzenia hosta. Aby to konfigurować serwera, takie jak **UseKestrel** jest. Usługi IIS za pomocą platformy ASP.NET Core, należy określić zarówno **UseKestrel** i **UseIISIntegration**. **Kestrel** jest przeznaczony do uruchamiania za serwerem proxy i nie powinny być wdrażane bezpośrednio połączonego z Internetem. **UseIISIntegration** określa usług IIS jako zwrotnego serwera proxy, ale jest to istotne tylko podczas uruchamiania na maszynach mających usług IIS. W przypadku wdrożenia aplikacji Windows, należy pozostawić go w. Go nie pogarszać inaczej.

    ![](media/netcore-image14.png)

6. Jest rozwiązaniem oczyszczarki do oddzielania ładowania ustawień uruchamiania aplikacji. Można to łatwo zrobić, **UseStartup** jest wywoływana, aby określić, że **uruchamiania** klasy jest wywoływany do ładowania ustawień i innych zadań uruchamiania, takich jak wstawianie oprogramowania pośredniczącego do potoku HTTP. Może mieć wielu **UseStartup** wywołania z założeniem, każdy z nich zastępuje poprzednie ustawienia zgodnie z potrzebami.

    ![](media/netcore-image15.png)

7. Ostatnim krokiem w tworzeniu **IWebHost** jest wywołanie **kompilacji**.

    ![](media/netcore-image16.png)

8. Podczas **IWebHost** klasy są wymagane do zaimplementowania nieblokującej na poziomie **Start**, projektów ASP.NET Core ma metodę rozszerzenia, o nazwie **Uruchom** to opakowuje  **Rozpocznij** z blokowanie kodu, dzięki czemu nie trzeba ręcznie uniemożliwić metody zamykania natychmiast.

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Zadanie 4. Uruchamianie i debugowanie aplikacji

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **CoreLab** węzeł projektu i wybierz pozycję **opcje**.

    ![](media/netcore-image18.png)

2. **Opcje projektu** okno dialogowe zawiera wszystko, czego potrzebujesz, aby dostosować, jak zbudowane i uruchomić aplikację. Wybierz **Uruchom > konfiguracje > domyślna** węzła z lewego panelu.

3. Sprawdź **Uruchom w konsoli zewnętrznej** i usuń zaznaczenie pola wyboru **Wstrzymaj dane wyjściowe konsoli**. Zazwyczaj samodzielnie hostowanej aplikacji nie miałoby jego konsoli, które są widoczne, ale zamiast tego będzie rejestrować wyników do **dane wyjściowe** konsoli. Na potrzeby tego laboratorium pokażemy je w oddzielnym oknie, mimo że nie trzeba to zrobić podczas normalnego rozwoju.

4. Kliknij przycisk **OK**.

    ![](media/netcore-image19.png)

5. Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację. Alternatywnie, można wybrać **Uruchom > Rozpocznij debugowanie**.

6. Program Visual Studio for Mac spowoduje uruchomienie dwa okna. Pierwsza to okna konsoli, która udostępnia wgląd w aplikację samodzielnie hostowanego serwera.

    ![](media/netcore-image20.png)

7. Drugim jest zwykłym oknie przeglądarki do testowania witryny. Chodzi o przeglądarce wie, ta aplikacja może być hostowanych w dowolnym miejscu. Kliknij przycisk **o** można przejść do tej strony.

    ![](media/netcore-image21.png)

8. Między innymi informacje o stronie renderuje część tekstu, ustaw w kontrolerze.

    ![](media/netcore-image22.png)

9. Zachowaj oba okna otwarte i z powrotem do programu Visual Studio dla komputerów Mac. Otwórz **Controllers/HomeController.cs** Jeśli nie jest już otwarty.

    ![](media/netcore-image23.png)

10. Ustaw punkt przerwania w pierwszym wierszu **o** metody. Można to zrobić, klikając na marginesie lub ustawia kursor myszy na wiersz i naciskając klawisz **F9**. Ten wiersz ustawia dane w **ViewData** kolekcji, który jest renderowany w stronę CSHTML pod **Views/Home/About.cshtml**.

    ![](media/netcore-image24.png)

11. Wróć do przeglądarki i Odśwież informacje o stronie. Wywoła to punkt przerwania w programie Visual Studio dla komputerów Mac.

12. Wskaźnik myszy nad **ViewData** elementu członkowskiego, aby wyświetlić jego dane. Można również rozwinąć jego elementów podrzędnych, aby wyświetlić dane zagnieżdżonych.

    ![](media/netcore-image25.png)

13. Usuń punkt przerwania aplikacji przy użyciu tej samej metody, użytego do ją dodać.

14. Otwórz **Views/Home/About.cshtml**.

15. Zmień tekst **"dodatkowe"** do **"zmienione"** i Zapisz plik.

    ![](media/netcore-image26.png)

16. Naciśnij klawisz **Kontynuuj** przycisk, aby kontynuować wykonywanie.

    ![](media/netcore-image27.png)

17. Wróć do okna przeglądarki, aby zobaczyć zaktualizowany tekst. Ta zmiana może odbywać się w dowolnym momencie i nie wymagają punktu przerwania w debugerze. Odśwież przeglądarkę, jeśli nie widzisz, zmiany zostaną uwzględnione natychmiast.

    ![](media/netcore-image28.png)

18. Zamknij konsolę programu test w przeglądarce okna i aplikacji. Spowoduje to zatrzymanie debugowania, jak również.

## <a name="task-5-application-startup-configuration"></a>Zadanie 5. Konfiguracja uruchamiania aplikacji

1. Z **Eksploratora rozwiązań**, otwórz **Startup.cs**. Można tutaj zauważyć pewne czerwone faliste linie początkowo jako pakiety NuGet są przywracane w tle i kompilator Roslyn tworzy pełny obraz zależności projektu.

    ![](media/netcore-image29.png)

2. Znajdź **uruchamiania** metody. Ta sekcja definiuje konfigurację wstępną dla aplikacji i gęsto spakowane. Omówmy tę kwestię w dół.

    ![](media/netcore-image30.png)

3. Metoda rozpoczyna się od zainicjowania **ConfigurationBuilder** i ustawianie jego ścieżki podstawowej.

    ![](media/netcore-image31.png)

4. Następnie ładuje wymaganą **appsettings.json** pliku.

    ![](media/netcore-image32.png)

5. Po tym próbuje załadować określonego środowiska **appsettings.json** pliku, który spowoduje zastąpienie istniejących ustawień. Na przykład, jest podana **appsettings. Development.JSON** plik używany w tym konkretnym środowisku. Aby dowiedzieć się więcej o konfiguracji w programie ASP.NET Core, zapoznaj się z [dokumentację](https://docs.microsoft.com/aspnet/core/fundamentals/configuration).

    ![](media/netcore-image34.png)

6. Na koniec zmienne środowiskowe są dodawane do konstruktora konfiguracji i konfiguracji jest wbudowana i ustaw do użycia.

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Zadanie 6. Wstawianie oprogramowania pośredniczącego aplikacji

1. Znajdź **Konfiguruj** method in Class metoda **uruchamiania** klasy. Jest to, gdzie całe oprogramowanie pośredniczące jest skonfigurowany tak, że może być wstawiony do potoku HTTP i używane do przetwarzania każdego żądania do serwera. Gdy ta metoda jest wywoływana tylko raz, zawartość metody (takie jak **UseStaticFiles**) mogą być wykonywane na każde żądanie.

    ![](media/netcore-image36.png)

2. Można również dodać dodatkowe oprogramowanie pośredniczące do wykonania w ramach potoku. Dodaj poniższy kod po **aplikacji. UseStaticFiles** do automatycznego dodawania **X-Test** nagłówka do każdej odpowiedzi wychodzącej. Funkcja IntelliSense ułatwia wykonania kodu podczas wpisywania.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Naciśnij klawisz **F5** Aby skompilować i uruchomić projekt.

4. Możemy użyć przeglądarki, aby sprawdzić nagłówki, aby sprawdzić, czy są one dodawane. Poniższe instrukcje dotyczą programu Safari, ale możesz dzieje się tak samo [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) lub [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console).

5. Po ładowane do przeglądarki przy lokacji, wybierz **Safari > Preferencje**.

6. Na **zaawansowane** karcie wyboru **pokazują tworzenie menu na pasku menu** i zamknij okno dialogowe.

    ![](media/netcore-image37.png)

7. Wybierz **opracowywanie > Pokaż zasoby strony**.

8. Odświeżenie okna przeglądarki, tak aby narzędzi deweloperskich w nowo otwartym mogą śledzić i analizowania ruchu sieciowego i zawartości.

9. Strony HTML localhost renderowana przez serwer będzie elementu wybrane domyślnie.

    ![](media/netcore-image38.png)

10. Rozwiń **paska bocznego szczegóły**.

    ![](media/netcore-image39.png)

11. Przewiń do dołu paska bocznego, aby wyświetlić nagłówek odpowiedzi, wcześniej dodany w kodzie.

    ![](media/netcore-image40.png)

12. Zamknij okno przeglądarki i konsoli, jeśli jest spełniony.

## <a name="summary"></a>Podsumowanie

W tym środowisku laboratoryjnym już wiesz, jak zacząć tworzenie aplikacji platformy ASP.NET Core z programem Visual Studio dla komputerów Mac. Jeśli chcesz, zapoznaj się z tworzeniem bardziej szczegółowy aplikacji bazy danych filmów, zobacz [Rozpoczynanie pracy z platformą ASP.NET Core MVC](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/start-mvc) samouczka.
