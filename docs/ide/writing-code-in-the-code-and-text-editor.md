---
title: Funkcje edytora kodu
ms.date: 02/23/2018
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de209e0a940fe7f7c64644cea37de3762df0d643
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588554"
---
# <a name="features-of-the-code-editor"></a>Funkcje edytora kodu

Edytor programu Visual Studio udostępnia wiele funkcji, które ułatwiają pisanie kodu i tekstu oraz zarządzanie nim. Można rozwinąć i zwinąć różne bloki kodu za pomocą konspektów. Więcej informacji na temat kodu można uzyskać za pomocą technologii IntelliSense, **przeglądarki obiektów**i hierarchii wywołań. Kod można znaleźć za pomocą funkcji, takich jak **Przejdź do**, Przejdź **do definicji**i **Znajdź wszystkie odwołania**. Można wstawiać bloki kodu za pomocą fragmentów kodu i generować kod przy użyciu funkcji, takich jak **Generowanie z użycia**. Jeśli edytor programu Visual Studio nigdy wcześniej nie był używany, zobacz [Dowiedz się, aby użyć edytora kodu.](../get-started/tutorial-editor.md)

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W przypadku programu Visual Studio dla komputerów Mac zobacz [Edytor źródła (Visual Studio dla komputerów Mac).](/visualstudio/mac/source-editor)

Kod można wyświetlić na wiele różnych sposobów. Domyślnie **Eksplorator rozwiązań** pokazuje kod uporządkowany według plików. Możesz kliknąć kartę **Widok klasy** w dolnej części okna, aby wyświetlić kod uporządkowany według klas.

Tekst można wyszukiwać i zamieniać w pojedynczych lub wielu plikach. Aby uzyskać więcej informacji, zobacz [Znajdowanie i zamienianie tekstu](../ide/finding-and-replacing-text.md). Do znajdowania i zamieniania tekstu można używać wyrażeń regularnych. Aby uzyskać więcej informacji, zobacz [Używanie wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Różne języki programu Visual Studio oferują różne zestawy funkcji, a w niektórych przypadkach funkcje zachowują się inaczej w różnych językach. Wiele z tych różnic są określone w opisach funkcji, ale aby uzyskać więcej informacji można zobaczyć sekcje w określonych językach programu Visual Studio.

## <a name="editor-features"></a>Funkcje edytora

|||
|-|-|
|Kolorowanie składni|Niektóre elementy składni plików kodu i znaczników są barwione inaczej, aby je odróżnić. Na przykład słowa kluczowe `using` (na przykład `Imports` w języku C# i Visual Basic) są jednym kolorem, ale typy (takie jak `Console` i `Uri`) są innym kolorem. Inne elementy składni są również pokolorowane, takie jak literały ciągów i komentarze. C++ używa koloru do rozróżniania typów, wyliczenia i makra, wśród innych tokenów.<br /><br /> W [oknie dialogowym Czcionki i Kolory, Środowisko, Opcje](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)można wyświetlić kolor domyślny dla każdego typu, a kolor dla dowolnego określonego elementu składni można otworzyć w menu **Czcionki** i kolory, Środowisko, Opcje.|
|Znaki błędów i ostrzeżeń|Podczas dodawania kodu i tworzenia rozwiązania, można zobaczyć (a) wymachiwania w różnych kolorach (znany jako squiggles) lub (b) żarówki pojawiające się w kodzie. Czerwone squiggles oznaczają błędy składniowe, niebieski oznacza błędy kompilatora, zielony oznacza ostrzeżenia, a fioletowy oznacza inne typy błędów. [Szybkie akcje](../ide/quick-actions.md) sugerują poprawki problemów i ułatwiają zastosowanie poprawki.<br /><br /> Domyślny kolor każdego błędu i ostrzeżenia można zobaczyć w oknie dialogowym**Environment** > **Czcionki i kolory** **opcji** >  **narzędzi.** >  **Poszukaj błędu składni,** **błędu kompilatora,** **ostrzeżenia**i **innego błędu**.|
|Dopasowywanie nawiasów klamrowych|Gdy punkt wstawiania jest umieszczony na otwartym nawiasie klamrowym w pliku kodu, zarówno on, jak i nawias zamykający są wyróżnione. Ta funkcja natychmiast informuje o zagubionych lub brakujących nawiasach klamrowych. Dopasowywanie nawiasów klamrowych można włączyć lub wyłączyć za pomocą ustawienia **Automatycznego wyróżniania ogranicznika** **(Edytor tekstu****Opcje** > **narzędzi).** >  Kolor podświetlenia można zmienić w ustawieniu **Czcionki i Kolory** **(Środowisko****opcji** > **narzędzi).** >  **Poszukaj dopasowania nawiasów klamrowych (podświetlenie)** lub **dopasowywania nawiasów klamrowych (prostokąt)**.|
|Wizualizator struktury|Linie kropkowane łączą pasujące nawiasy klamrowe w plikach kodu, ułatwiając widzenie par nawiasów klamrowych otwierających i zamykających. Może to pomóc w znalezieniu kodu w bazie kodu szybciej. Te wiersze można włączyć lub wyłączyć za pomocą **wskazówek Pokaż strukturę** w sekcji **Wyświetlanie** na stronie**Ogólne** **Edytor** > tekstu**Opcje** >  **narzędzi.** > |
|Numery wierszy|Numery wierszy mogą być wyświetlane na lewym marginesie okna kodu. Nie są one wyświetlane domyślnie. Tę opcję można włączyć w **ustawieniach Edytora tekstu Wszystkie języki** **(Opcje narzędzi** > **Options** > **Edytor** > tekstu**Wszystkie języki**). Numery wierszy dla poszczególnych języków programowania można wyświetlić, zmieniając ustawienia dla tych języków **(Opcje narzędzi** > **Options** > **edytor** > **\< **tekstu>). Aby można było wydrukować numery wierszy, należy wybrać **opcję Dołącz numery wierszy** w oknie dialogowym **Drukowanie.**|
|Śledzenie zmian|Kolor lewego marginesu umożliwia śledzenie zmian wprowadzonych w pliku. Zmiany wprowadzone od momentu otwarcia pliku, ale nie zostały zapisane, są oznaczane żółtym paskiem na lewym marginesie (zwanym marginesem zaznaczenia). Po zapisaniu zmian (ale przed zamknięciem pliku) pasek zmieni kolor na zielony. Jeśli po zapisaniu pliku zostanie cofnięta zmiana, pasek zmieni kolor na pomarańczowy. Aby wyłączyć i włączyć tę funkcję, zmień opcję **Śledź zmiany** w ustawieniach **edytora tekstu** **(Narzędzia** > **Opcje** > **Edytor tekstu**).|
|Zaznaczanie kodu i tekstu|Tekst można zaznaczać w standardowym trybie strumienia ciągłego lub w trybie pudełkowym, w którym zamiast zestawu wierszy jest wybierana prostokątna część tekstu. Aby dokonać zaznaczenia w trybie pola, naciśnij klawisz **Alt** podczas przeciągania myszy nad zaznaczeniem (lub naciśnij**\<klawisz strzałki ** **Alt**+**Shift**+>). Zaznaczenie zawiera wszystkie znaki w prostokącie zdefiniowane przez pierwszy znak i ostatni znak w zaznaczeniu. Wszystko wpisywane lub wklejane do zaznaczonego obszaru jest wstawiane w tym samym punkcie w każdym wierszu.|
|Zoom|Możesz powiększać lub pomniejszać w dowolnym oknie kodu, naciskając i przytrzymując klawisz **Ctrl** i przesuwając kółko przewijania myszy (lub **Ctrl**+**Shift**+**.** i **Ctrl**+**Shift**+**,** aby zmniejszyć). Można również użyć pola **Powiększenie** w lewym dolnym rogu okna kodu, aby ustawić określoną wartość procentową powiększenia. Funkcja powiększenia nie działa w oknach narzędzi.|
|Przestrzeń wirtualna|Domyślnie wiersze w edytorach programu Visual Studio kończą się po ostatnim znaku, dzięki czemu klawisz **strzałki** w prawo na końcu wiersza przenosi kursor na początek następnego wiersza. W niektórych innych edytorach wiersz nie kończy się po ostatnim znaku i można umieścić kursor w dowolnym miejscu w wierszu. Przestrzeń wirtualną można włączyć w edytorze w ustawieniach**Edytor tekstu** >  **Narzędzia** > **Opcje** > tekstu**Wszystkie języki.** Należy zauważyć, że można włączyć **przestrzeń wirtualną** lub **zawijanie wyrazów,** ale nie oba.|
|Drukowanie|Za pomocą opcji w oknie dialogowym **Drukowanie** można uwzględnić numery wierszy lub ukryć zwinięte obszary kodu podczas drukowania pliku. W oknie dialogowym **Ustawienia strony** można również wydrukować pełną ścieżkę i nazwę pliku, wybierając **nagłówek strony**.<br /><br /> Opcje drukowania kolorów można ustawić w oknie dialogowym**Environment** > **Czcionki i kolory** **opcje środowiska** >  **narzędzia.** >  Wybierz **pozycję Drukarka** na liście **Pokaż ustawienia do** dostosowania drukowania w kolorze. Można określić inne kolory drukowania pliku niż do edycji pliku.|
|Cofanie i ponawianie ponawianie w globalnym dziele|Polecenia **Cofnij ostatnią akcję globalną** i **Ponawiaj ostatnią akcję globalną** w menu **Edycja** cofaj lub ponawiaj akcje globalne, które mają wpływ na wiele plików. Akcje globalne obejmują zmianę nazwy klasy lub obszaru nazw, wykonywanie operacji znajdowania i zamieniania w rozwiązaniu, refaktoryzowanie bazy danych lub inne działania, które zmieniają wiele plików. Globalne polecenia cofania i ponawiania do akcji w bieżącej sesji programu Visual Studio można zastosować nawet po zamknięciu rozwiązania, w którym zastosowano akcję.|

## <a name="advanced-editing-features"></a>Zaawansowane funkcje edycji

W menu **Edycja** > **zaawansowane** można znaleźć wiele zaawansowanych funkcji na pasku narzędzi. Nie wszystkie z tych funkcji są dostępne dla wszystkich typów plików kodu.

|||
|-|-|
|Formatuj dokument|Ustawia prawidłowe wcięcie wierszy kodu i przenosi nawiasy klamrowe do oddzielnych wierszy w dokumencie.|
|Formatowanie zaznaczenia|Ustawia prawidłowe wcięcie wierszy kodu i przenosi nawiasy klamrowe do oddzielnych linii w zaznaczeniu.|
|Tabify zaznaczone wiersze|W razie potrzeby zmienia spacje wiodące na karty.|
|Ujednolicenie zaznaczonych wierszy|Zmienia wiodące karty na spacje. Jeśli chcesz przekonwertować wszystkie spacje w pliku na karty (lub wszystkie `Edit.ConvertSpacesToTabs` karty `Edit.ConvertTabsToSpaces` na spacje), możesz użyć poleceń i. Te polecenia nie są wyświetlane w menu programu Visual Studio, ale można je wywołać w oknie **szybki dostęp** lub w oknie polecenia.|
|Wielkie litery|Zmienia wszystkie znaki w zaznaczeniu na wielkie litery lub jeśli nie ma zaznaczenia, zmienia znak w punkcie wstawiania na wielkie litery. Skrót: **Ctrl**+**Shift**+**U**.|
|Zrób małe litery|Zmienia wszystkie znaki w zaznaczeniu na małe litery lub jeśli nie ma zaznaczenia, zmienia znak w punkcie wstawiania na małe. Skrót: **Ctrl**+**U**.|
|Przenoszenie zaznaczonych linii w górę|Przesuwa zaznaczoną linię o jeden wiersz w górę. Skrót: **Alt**+**Strzałka w górę**.|
|Przenoszenie zaznaczonych linii w dół|Przesuwa zaznaczoną linię o jeden wiersz w dół. Skrót: **Alt**+**Strzałka w dół**.|
|Usuń poziomą biały spację|Usuwa karty lub spacje na końcu bieżącego wiersza. Skrót: **Ctrl**+**K**, **Ctrl**+**\\**|
|Zobacz biały spacja|Wyświetla spacje jako podniesione kropki, a karty jako strzałki. Koniec pliku jest wyświetlany jako prostokątny glif. Jeśli **zaznaczone** > jest**opcja Narzędzia** > Edytor > **tekstu****Wszystkie języki Zawijanie** > **Word Wrap** > **wyrazów Pokaż widoczne glify dla zawijania wyrazów,** ten glif jest również wyświetlany.|
|Zawijanie wierszy|Powoduje, że wszystkie wiersze w dokumencie są widoczne w oknie kodu. Zawijanie wyrazów można wyłączyć i włączyć w **ustawieniach Edytora tekstu Wszystkie języki** **(Opcje narzędzi** > **Options** > **Edytor** > tekstu**Wszystkie języki**).|
|Wybór komentarza|Dodaje znaki komentarza do zaznaczenia lub bieżącego wiersza. Skrót: **Ctrl**+**K**, **Ctrl**+**C**|
|Niekomentuj wyboru|Usuwa znaki komentarza z zaznaczenia lub bieżącego wiersza. Skrót: **Ctrl**+**K**, **Ctrl**+**U**|
|Zwiększ wcięcie wiersza|Dodaje kartę (lub równoważne spacje) do zaznaczonych linii lub bieżącego wiersza.|
|Zmniejsz wcięcie wiersza|Usuwa kartę (lub równoważne spacje) z zaznaczonych linii lub bieżącego wiersza.|
|Wybierz pozycję Znacznik|W dokumencie zawierającym znaczniki (na przykład XML lub HTML) wybiera znacznik.|
|Wybierz zawartość znacznika|W dokumencie zawierającym znaczniki (na przykład XML lub HTML) wybiera zawartość.|

## <a name="navigate-and-find-code"></a>Nawigowanie i znajdowanie kodu

Można poruszać się w edytorze kodu na kilka różnych sposobów, w tym nawigowanie do tyłu i do przodu do poprzednich punktów wstawiania, wyświetlanie definicji typu lub elementu członkowskiego i przechodzenie do określonej metody za pomocą paska nawigacyjnego. Aby uzyskać więcej informacji, zobacz [Nawiguj po kodzie](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Znajdowanie odwołań w bazie kodu

Aby dowiedzieć się, dokąd odnoszą się określone elementy kodu w całej bazie kodu, można użyć polecenia **Znajdź wszystkie odwołania** lub nacisnąć klawisz **Shift**+**F12**. Ponadto po kliknięciu typu lub elementu członkowskiego funkcja **wyróżniania odwołuje się** automatycznie wyróżnia wszystkie odwołania do tego typu lub elementu członkowskiego. Aby uzyskać więcej informacji, zobacz [Znajdowanie odwołań w kodzie](finding-references.md).

## <a name="customize-the-editor"></a>Dopasowywanie edytora

Ustawienia programu Visual Studio można udostępnić innemu deweloperowi, dostosować ustawienia do standardu lub powrócić do ustawień domyślnych programu Visual Studio za pomocą polecenia **Kreatora importu i eksportu** w menu **Narzędzia.** W **Kreatorze importu i eksportu można**zmienić wybrane ustawienia ogólne lub ustawienia języka i projektu.

Aby zdefiniować nowe skróty klawiszowe lub ponownie zdefiniować istniejące skróty klawiszowe, przejdź do**klawiatury** **narzędzia** > **Opcje** > **środowiska** > . Aby uzyskać więcej informacji na temat skrótów klawiszowych, zobacz [Domyślne skróty klawiaturowe](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Aby uzyskać opcje edytora specyficzne dla języka JavaScript, zobacz [Opcje edytora JavaScript](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Zobacz też

- [Edytor źródłowy (Visual Studio dla komputerów Mac)](/visualstudio/mac/source-editor)
- [Visual Studio IDE](../get-started/visual-studio-ide.md)
- [Wprowadzenie do języka C++ w programie Visual Studio](/cpp/get-started/tutorial-console-cpp)
- [Wprowadzenie do języka C# i ASP.NET w programie Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)
- [Wprowadzenie do języka Python w programie Visual Studio](../ide/quickstart-python.md)
