---
title: Zmienianie dziennika (Visual Studio Tools for Unity) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: d847d4dcd4ae2edd799c282d43ec717ca8ae0a71
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663508"
---
# <a name="change-log-visual-studio-tools-for-unity"></a>Dziennik zmian (Visual Studio Tools for Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dziennik zmian w programie Visual Studio Tools for Unity.

## <a name="23"></a>2.3
 Wydana 2016-07-14

### <a name="new-features"></a>Nowe funkcje

-   **Ogólne:**

    -   Dodano możliwość wyłączenia konsoli Unity dzienniki w liście błędów Visual Studio.

    -   Dodano opcję Zezwalaj na właściwości wygenerowanego projektu do zmodyfikowania.

-   **Debuger:**

    -   Ciąg wizualizatorów, dodano tekstu XML, HTML i JSON.

-   **Kreatorów:**

    -   Dodano brakujący MonoBehaviors.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Ogólne:**

    -   Rozwiązano konflikt z ReSharper, uniemożliwiającą kontrolek w Visual Studio, ustawienia będą wyświetlane.

    -   Rozwiązano konflikt ze środowiskiem Xamarin, który uniemożliwia debugowania w niektórych przypadkach.

-   **Debuger:**

    -   Rozwiązano problem powodujący zablokowanie podczas debugowania programu Visual Studio.

    -   Rozwiązano problem z punktów przerwania funkcji w programie Visual Studio 2015.

    -   Rozwiązano wyrażenie kilka problemów oceny.

## <a name="22"></a>2.2
 Wydana 2016-02-04

### <a name="new-features"></a>Nowe funkcje

-   **Kreatorów:**

    -   Dodano inteligentne wyszukiwanie w **MonoBehavior Implementowanie** kreatora.

    -   Świadomość; kontekst jako kreatorzy na przykład NetworkBehavior komunikaty są dostępne tylko podczas pracy z NetworkBehavior.

    -   Dodano obsługę komunikatów NetworkBehavior w kreatorach.

-   **INTERFEJS UŻYTKOWNIKA:**

    -   Dodano opcję, aby skonfigurować widoczność MonoBehavior wiadomości.

    -   Usunięte stron właściwości programu Visual Studio, które nie są ważnego do projektów aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Generowanie projektu:**

    -   Naprawiono odwołania do UnityEngine i UnityEditor na 4.6 aparatu Unity.

    -   Naprawiono Generowanie plików projektu, gdy Unity jest uruchomiony w systemie OSX.

    -   Naprawiono obsługi nazwy projektu zawierające znaki hashmark (#).

    -   Ograniczony wygenerowane projekty, do 4 C#.

-   **Debuger:**

    -   Rozwiązano problem z obliczanie wyrażeń podczas debugowania w koprocedury aparatu Unity.

    -   Rozwiązano problem powodujący zablokowanie podczas debugowania programu Visual Studio.

-   **INTERFEJS UŻYTKOWNIKA:**

    -   Naprawiono niezgodność z [Studio karty](https://tabsstudio.com/) rozszerzenia programu Visual Studio.

-   **Instalator:**

    -   Obsługuje instalację komputera VSTU (Instalacja dla wszystkich użytkowników), tworząc wpisy rejestru HKLM.

    -   Rozwiązane problemy dezinstalacji VSTU po zainstalowaniu tej samej wersji w narzędziach VSTU dla wielu różnych wersji programu Visual Studio. Na przykład, gdy w narzędziach VSTU **2015** 2.1.0.0 i w narzędziach VSTU **2013** 2.1.0.0 zostały zainstalowane.

## <a name="21"></a>2.1
 Wydana 2015-09-08

### <a name="new-features"></a>Nowe funkcje

-   Obsługa aparatu Unity 5.2

### <a name="bug-fixes"></a>Poprawki błędów

-   Wyświetlanie elementów menu w Unity < 4.2

-   Komunikat o błędzie nie będzie już wyświetlany w przypadku programu Visual Studio blokuje pliki intellisense XML.

-   Obsługa <\<po zmianie >> warunkowe punkty przerwania, gdy argument warunkowy nie jest wartością logiczną.

-   Naprawiono odwołania do zestawów UnityEngine i UnityEditor dla aplikacji Windows Store.

-   Naprawiono błąd przy przechodzeniu w debugerze: Nie można przejść, ogólny wyjątek.

-   Stałej liczby trafień punkty przerwania w programie Visual Studio 2015.

## <a name="20"></a>2.0
 Wydana 2015-07-20

### <a name="bug-fixes"></a>Poprawki błędów

-   **Integracja aparatu Unity:**

    -   Naprawiono konwersji symbole debugowania utworzonych za pomocą programu Visual Studio 2015, podczas importowania biblioteki DLL i jego symboli debugowania (PDB).

    -   Zawsze generuj pliki MDB podczas importowania biblioteki DLL i jego symboli debugowania (PDB), z wyjątkiem sytuacji, gdy podano również pliku MDB.

    -   Naprawiono zanieczyszczeniu katalogu projektu środowiska Unity za pomocą katalogu.

    -   Naprawiono Generowanie odwołania do System.Xml.Link i System.Runtime.Serialization.

    -   Punkty zaczepienia dodano obsługę wielu subskrybentów do generowania plików projektu interfejsu API.

    -   Generowanie pliku zawsze kompletnego projektu nawet wtedy, gdy jeden z plików do wygenerowania jest zablokowany.

    -   Dodano obsługę * symboli wieloznacznych w rozszerzeniu filtrowanie podczas określania plików, które mają zostać uwzględnione w projekcie języka C#.

-   **Integracja z programem Visual Studio:**

    -   Rozwiązano problem ze zgodnością z Productivity Power Tools.

    -   Naprawiono Generowanie MonoBehaviors wokół deklaracji zdarzeń i delegatów.

-   **Debuger:**

    -   Naprawiono potencjalne blokowanie, podczas debugowania.

    -   Rozwiązano problem, w której elementy lokalne, nie będzie wyświetlana w niektórych ramek stosu.

    -   Naprawiono sprawdzania pusty tablic.

## <a name="20-preview-2"></a>2.0 w wersji zapoznawczej 2
 Wydana 2015-04-02

### <a name="new-features"></a>Nowe funkcje

-   **Eksplorator projektu środowiska Unity:**

    -   Automatycznie Zmień nazwę klasy, zmieniając nazwę pliku w Eksploratorze projektów aparatu Unity (zobacz **opcje** okna dialogowego).

    -   Automatycznie wybierz nowo utworzony skryptów w Eksploratorze projektów aparatu Unity.

    -   Śledzenie aktywnych skryptów w Eksploratorze projektów aparatu Unity (zobacz **opcje** okna dialogowego).

    -   Dual — Synchronizuj Eksploratorze rozwiązań programu Visual Studio (zobacz **opcje** okna dialogowego).

    -   Przyjęcie ikony programu Visual Studio w Eksploratorze projektów aparatu Unity.

-   **Debuger:**

    -   Wybierz cel debugowania aktywnego listę celów debugowania zapisana lub ostatnio używanych (zobacz **opcje** okna dialogowego).

    -   Utwórz punkty przerwania funkcji w metodach MonoBehavior i zastosować je do wielu klas MonoBehavior.

    -   Obsługa wprowadzić identyfikator obiektu w debugerze.

    -   Obsługa liczba w debugerze trafień punktu przerwania.

    -   Obsługuje podział na wyjątek w debugerze (eksperymentalne. Zobacz **opcje** okna dialogowego).

    -   Obsługuje tworzenie obiekty i tablice podczas obliczania wyrażenia w debugerze.

    -   Obsługuje porównania wartości null podczas oceny wyrażenia w debugerze.

    -   Odfiltruj przestarzałe składowe w oknach wyrażenie kontrolne debugera.

-   **Instalator:**

    -   Zoptymalizowane Visual Studio Tools for Unity Rejestracja rozszerzenia.

    -   Zainstaluj program Visual Studio Tools dla pakietu Unity dla aparatu Unity 5.

-   **Dokumentacja:** Zwiększ wydajność Generowanie dokumentacji.

-   **Kreatorów:** Obsługa nowych metod MonoBehavior Unity 4.6 i aparatu Unity 5.

-   **Unity:** Flagi niebezpieczne wyszukiwania i niestandardowych definiuje .rsp — pliki podczas generowania pliku projektu.

-   **INTERFEJS UŻYTKOWNIKA:** Dodano program Visual Studio Tools for Unity **opcje** okna dialogowego w programie Visual Studio.

### <a name="bug-fixes"></a>Poprawki błędów

-   **Eksplorator projektu środowiska Unity:**

    -   Odśwież Eksploratora projektów aparatu Unity po pliki są przesyłane lub zmieniono jego nazwę w Eksploratorze rozwiązań programu Visual Studio.

    -   Zachowaj opcje podczas zmieniania nazw plików w Eksploratorze projektów aparatu Unity.

    -   Uniemożliwić automatyczne rozwijać i zwijać gdy pliki są podwójnego kliknięcia w Eksploratorze projektów aparatu Unity.

    -   Upewnij się, że nowo wybrane pliki są widoczne w Eksploratorze projektów aparatu Unity.

-   **Debuger:**

    -   Uniemożliwia to możliwe, Zablokuj programu Visual Studio, podczas obliczania wyrażenia w debugerze.

    -   Upewnij się, że wywołania metod powinny być wykonywane dla domeny w debugerze.

-   **Unity:**

    -   Popraw lokalizację UnityVS.OpenFile za pomocą aparatu Unity 5.

    -   Popraw lokalizację pdb2mdb za pomocą aparatu Unity 5.

    -   Zapobiegaj możliwym wyjątkiem podczas generowania pliku projektu.

    -   Zapobiegaj możliwe blokowanie, podczas uruchamiania aparatu Unity w systemie OSX.

    -   Obsługa wyjątków wewnętrznych.

    -   Wyślij dzienniki konsoli Unity do listy błędów programu VS.

-   **Dokumentacja:** Generowanie dokumentacji poprawne dla nowej dokumentacji aparatu unity.

-   **Projekt:** Przenieś i Zmień nazwy plików .meta Unity w razie potrzeby, nawet w przypadku folderów.

-   **Kreatorów:** Popraw kolejność parametrów metody MonoBehavior podczas generowania kodu.

-   **INTERFEJS UŻYTKOWNIKA:** Obsługa kompozycji programu Visual Studio ikony i menu kontekstowego.

## <a name="20-preview"></a>W wersji 2.0 (wersja zapoznawcza)
 Wydana 2014-11-12

### <a name="new-features"></a>Nowe funkcje

-   Pomoc techniczna dla programu Visual Studio 2015.

-   Barwy kodu dla aparatu Unity programów do cieniowania programu Visual Studio 2015.

-   Ulepszone wizualizacji wartości podczas debugowania:

    -   Lepszą wizualizację ArrayLists, list, tabele i słowników.

    -   Pokaż niepubliczne elementy członkowskie i statyczne elementy członkowskie jako kategorii w wyrażenie kontrolne i lokalnych widokach.

    -   Ulepszone wyświetlanie SerializedProperty mechanizmu Unity do oceny, tylko pola wartość, które jest nieprawidłowa dla właściwości.

    -   Debuggerdisplayattribute — Obsługa klas i struktur.

    -   Debuggertypeproxyattribute — pomoc techniczna.

-   Należy wstawiania obiekt MonoBehaviour metody przy użyciu naszej kreatorów w celu uwzględniania użytkownika konwencje kodowania.

-   Implementuje obsługę szablony tekstowe czasu kompilacji w projektach UnityVS wygenerowany.

-   Implementuje obsługę zasobów ResX w projektach UnityVS wygenerowany.

-   Obsługa otwierania programów do cieniowania w programie Visual Studio z poziomu aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

-   Oczyszczanie gniazd przed rozpoczęciem gry na platformie Unity po Dołącz i odtwarzania zostały wyzwolone w programie Visual Studio. To naprawia pewne problemy z stabilności połączenia między Unity i programu VS, podczas korzystania z Dołącz i odtwarzania.

-   Należy unikać wywoływania metod w interfejsie debuger aparatu skryptów mechanizmu Unity, które są podatne na blokowanie aparatu Unity. To naprawia blokowanie aparatu Unity podczas dołączania debugera.

-   Napraw, wyświetlanie elementu stosy wywołań, jeśli brak symboli nie są dostępne.

-   Nie rejestruj wywołanie zwrotne dziennika, jeśli nie mamy.

## <a name="192"></a>1.9.2
 Wydana 2014-10-09

### <a name="new-features"></a>Nowe funkcje

-   Zwiększ wykrywania graczy aparatu Unity.

-   Korzystając z naszych użytkownika otwierającego plik, należy Unity przekazać numer wiersza, a także nazwę pliku.

-   Domyślnie się z dokumentacją online platformy Unity, jeśli nie lokalną dokumentację.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono awarię Unity, gdy aktywacja punktu przerwania po domeny Załaduj ponownie.

-   Usuń wyjątki przedstawione w konsoli platformy Unity podczas zamykania naszym konfiguracji lub dotyczące systemu windows, po nazwie domeny Załaduj ponownie.

-   Napraw wykrywania Unity 64-bitowy, uruchamiane lokalnie.

-   Usuń filtrowanie Monobehaviour poszczególnych wersji aparatu Unity w kreatorach.

-   Naprawiono błąd, w którym wszystkie zasoby zostały uwzględnione w plikach projektu, jeśli filtr rozszerzeń był pusty.

## <a name="191"></a>1.9.1
 Wydana 22-2014-09

### <a name="new-features"></a>Nowe funkcje

-   Optymalizuj powiązania punktu przerwania w lokalizacji źródłowej.

-   Pomoc techniczna dla przeciążonych metod obliczania wyrażeń debugera.

-   Obsługa podstawowych pakowania i typy wartości obliczania wyrażeń debugera.

-   Obsługa ponownego tworzenia środowiska zmienne lokalne języka C#, podczas debugowania metod anonimowych.

-   Usuń, a następnie zmień nazwy plików .meta podczas usuwania lub zmiany nazwy plików w programie Visual Studio.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono obsługę motywów programu Visual Studio. Wcześniej okien dialogowych na czarny motywy może być pusty.

-   Naprawiono blokowanie aparatu Unity, gdy połączenie ze debugera przy jednoczesnej konieczności ponownego kompilowania aparatu Unity.

-   Usuń punkty przerwania podczas debugowania zdalnego edytory lub graczy skompilowany w innym systemie.

-   Naprawiono ewentualnej awarii programu Visual Studio, gdy punkt przerwania zostaje trafiony.

-   Punkty przerwania napraw powiązania w celu uniknięcia punktów przerwania, przedstawiający jako zwolniony.

-   Naprawiono obsługę zakres zmiennej w debugerze, aby uniknąć zmiennych na żywo, które pojawiają się poza zakresem.

-   Napraw wyszukiwania statyczne elementy członkowskie obliczania wyrażeń debugera.

-   Napraw, wyświetlania typów obliczania wyrażeń debugera, aby wyświetlić właściwości i pola statyczne.

-   Naprawiono Generowanie rozwiązania, gdy nazwy projektów aparatu Unity zawiera znaki specjalne, że program Visual Studio zabrania (Połącz problem #948666).

-   Napraw pakiet Visual Studio Tools Unity, aby natychmiast zatrzymać wysyłanie zdarzenia konsoli po opcji unchecked (Połącz problem #933357).

-   Napraw wykrywania odwołania do odwołania do nowych interfejsów API, takich jak UnityEngine.UI w projektach UnityVS wygenerowany został poprawnie wygenerowany.

-   Napraw Instalator, aby wymagać, że program Visual Studio jest zamknięty przed rozpoczęciem instalacji, aby uniknąć uszkodzone instalacje.

-   Napraw Instalatora w celu zainstalowania zestawy odwołań Unity jako składnik odpowiednie autonomiczne, współużytkowana przez wszystkie wersje narzędzi vstu.

-   Poprawka otwieranie skryptów za pomocą rozszerzenia VSTU w 64-bitowej wersji aparatu Unity.

## <a name="19"></a>1.9
 Wydana 2014-07-29

### <a name="new-features"></a>Nowe funkcje

-   W oknie Dołącz debuger aparatu Unity dodanie możliwości do wprowadzania niestandardowego adresu IP i portu do debugowania.

-   Dodaj opcję konfiguracji, aby ustawić Unity do uruchamiania w tle, czy nie.

-   Dodaj opcję konfiguracji, aby wygenerować pliki rozwiązań i projektów lub tylko plików projektu.

-   Docelowy uruchamiania: Dołącz do aparatu Unity lub Dołącz do aparatu Unity i Odtwórz.

-   Wyświetlanie tablic wielowymiarowych w debugerze.

-   Obsługa nowych Unity Player debugowania portów.

-   Uchwyt odwołania do zestawów aparatu Unity, nowe, takich jak mechanizmu Unity 4.6 zestawy graficznego interfejsu użytkownika.

-   Deconstructs wolnych od pracy do prawidłowego wyświetlenia zmiennych lokalnych podczas debugowania.

-   Podczas debugowania, deconstructs zmienne wygenerowanego Iteratory do argumentów.

-   Zachowaj stan Eksploratora projektów aparatu Unity po Załaduj ponownie projekt.

-   Dodaj polecenie Synchronizuj Eksploratora projektów aparatu Unity za pomocą bieżącego dokumentu.

### <a name="bug-fixes"></a>Poprawki błędów

-   Napraw warunkowe punkty przerwania, których warunki są ustawiane przed rozpoczęciem debugowania.

-   Usuń odwołania do UnityEngine w celu uniknięcia ostrzeżeń.

-   Napraw analizy wersje dla aparatu Unity w wersji beta.

-   Rozwiązać problem, gdy zmienne nie było wyświetlane w oknie zmienne lokalne, po naciśnięciu klawisza punkt przerwania lub przechodzenie krok po kroku.

-   Napraw zmienne etykietki narzędzi w programie Visual Studio 2013.

-   Naprawiono Generowanie dokumentacji funkcji IntelliSense dla aparatu Unity 4.5.

-   Napraw Unity / komunikacji programu Visual Studio po domeny Załaduj ponownie (na platformie Unity Odtwórz/Zatrzymaj).

-   Naprawiono obsługę części kompozycji programu Visual Studio.

> [!IMPORTANT]
>  C# jest dominujący języka należący do ekosystemu platformy Unity — nowe zasoby próbki są w języku C#, będą domyślnie dokumentacja aparatu Unity C# — usunęliśmy naszych podstawowa pomoc techniczna dla UnityScript i coś lepiej skoncentrować się na środowisko C#. W wyniku VSTU rozwiązania są teraz C# tylko i szybciej, aby załadować.

## <a name="182"></a>1.8.2
 Wydana 2014 01-07-

### <a name="new-features"></a>Nowe funkcje

-   Obejść problem w warstwie sieci firmy Unity silnik wykonywania skryptów w Mavericks zdalnego odnajdywania edytorów.

-   Obsługa nowych portów, aby odnaleźć zdalnego graczy aparatu Unity.

-   Odwołanie do określonego zestawu UnityEngine do bieżącego kompilacji docelowej.

-   Dodaj ustawienie, aby odfiltrować pliki do uwzględnienia w wygenerowanym projektów.

-   Dodaj ustawienie, aby wyłączyć wysyłanie dzienników konsoli, na liście błędów Visual Studio. Jest to przydatne, jeśli używasz PlayMaker lub konsoli Pro, ponieważ może istnieć tylko jedno wywołanie zwrotne zarejestrowane na platformie Unity, aby otrzymać dzienniki konsoli.

-   Dodaj ustawienie, aby wyłączyć generowanie symboli debugowania mdb. Jest to przydatne, jeśli generowania mdb samodzielnie.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono regresję, gdy pliki otwarte w programie VS środowiska Unity > = 4.2 spowoduje utratę funkcji IntelliSense.

-   Napraw naszych okien dialogowych programu VS, do obsługi motywy niestandardowe.

-   Poprawka menu kontekstowe UPE zamknięcia.

-   Zapobiegania awarii na platformie Unity po określonej wersji wygenerowanego zestawu, jeśli są one zsynchronizowane.

## <a name="181"></a>1.8.1
 Wydana 2013-11-21

### <a name="new-features"></a>Nowe funkcje

-   Dostosowane kreatorów obiekt MonoBehaviour za pomocą interfejsów API 4.3 aparatu Unity.

-   Obiekt MonoBehaviour kreatorów filtrowania w zależności od używanej wersji interfejsów API aparatu Unity.

-   Dodaj odwołanie do System.Xml.Linq do projektów dla aparatu Unity > 4.1.

-   Prettify naszych wywołania czy wykluczającą początku stacktrace w komunikacie.

### <a name="bug-fixes"></a>Poprawki błędów

-   Usunięto usterkę, w których firma Microsoft będzie zakłócać domyślna obsługa plików JavaScript w programie Visual Studio.

-   Naprawiono białe pikseli, pojawiają się w programie VS rzeczywiste tym razem.

-   Naprawiono usunięcie zestawu UnityVS.VersionSpecific, jeśli jest oznaczony jako tylko do odczytu przez Menedżer sterowania usługami.

-   Naprawiono wyjątki podczas tworzenia gniazda w pakiecie UnityVS.

-   Naprawiono awarię programu Visual Studio, podczas ładowania obrazów podstawowych z zestawów programu Visual Studio.

-   Usunięto usterkę w generacji UnityVS.VersionSpecific źródła kompilacji aparatu Unity.

-   Naprawiono możliwe blokowanie, podczas otwierania gniazda w pakiecie aparatu Unity.

-   Naprawiono obsługę projektów aparatu Unity kreską (-) w swojej nazwie.

-   Naprawiono otwieranie skryptów środowiska Unity w celu nie należy mylić kolejności ALT + TAB dla aparatu Unity 4.2 lub nowszej.

## <a name="180"></a>1.8.0
 Wydana 2013-09-24

### <a name="new-features"></a>Nowe funkcje

-   Znacznie zwiększona szybkość połączenia debugera.

-   Automatycznie obsługiwać nawigację do pliku i wierszu Unity 4.2 lub nowszej.

-   Warunkowe punkty przerwania.

-   Generator pliku projektu teraz obsługuje szablony T4.

-   Zaktualizuj kreatorów MonBehavior przy użyciu nowych interfejsów API.

-   Dokumentacja funkcji IntelliSense w języku C# dla typów aparatu Unity.

-   Obliczanie wyrażenia arytmetycznych i logicznych.

-   Lepsze odnajdywanie zdalnego edytorów dla zdalnego debugowania w wersji zapoznawczej.

### <a name="bug-fixes"></a>Poprawki błędów

-   Usunięto usterkę której firma Microsoft będzie przecieku wątku w programie VS po odłączeniu debugera.

-   Naprawiono białe pikseli, pojawiają się w programie VS.

-   Stała obsługi kliknięcia na ikonę paska stanu.

-   Naprawiono Generowanie odwołania do zestawów w folderach wtyczek.

-   Naprawiono Tworzenie gniazda z pakietu UnityVS w przypadku wyjątków.

-   Naprawiono wykrywania nowych wersji UnityVS.

-   Naprawiono monit Menedżera licencji po wygaśnięciu licencji.

-   Naprawiono usterkę, która może uniemożliwić listę procesów pusty w debugerze Dołącz do procesu okna programu VS.

-   Zmienianie wartościami stałymi obliczające w widoku lokalny.

## <a name="122"></a>1.2.2
 Wydana 2013-07-09

### <a name="bug-fixes"></a>Poprawki błędów

-   Obsługują w pełni kwalifikowane nazwy w ewaluatorze wyrażeń.

-   Stała blokowanie związane z obsługą wyjątków, gdy aparat skryptów Unity wysyła nam stackframe nieprawidłowe dane.

-   Naprawiono procesu kompilacji dla celów sieci Web.

-   Naprawiono błąd, który może się zdarzyć, jeśli został uruchomiony w programie Visual Studio i usunięty plik był na liście plików, aby otworzyć przy uruchamianiu.

-   Naprawiono UnityVS.OpenFile do obsługi plików bez skryptów, takich jak skompilowane programy do cieniowania.

-   Firma Microsoft teraz odwoływać się do Boo.Lang i UnityScript.Lang ze wszystkich projektów języka C#.

-   Naprawiono Generowanie odwołania w projektach, jeśli projekt zawiera znaki specjalne.

-   Obejście VS problem gdzie wywołania metody do usunięty projektów powodowało wielu MessageBox obiektu NullReferenceException.

-   Naprawiono obsługi zestawów 4.2 Unity w wersji Beta.

## <a name="121"></a>1.2.1
 Wydana 2013-04-09

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono lokalne Wdrażanie zestawów aparatu Unity do uzupełniania kodu w przypadku wystąpienia błędu We/Wy (takich jak pliki tylko do odczytu, lub pliki zablokowane przez program Visual Studio).

-   Naprawiono regresję, gdzie otworzenie skryptu środowiska Unity będzie koncentruje się plik, jeśli został on już otwarty w programie Visual Studio.

-   Rozwiązano problem z wydajnością dla nowych obsługi wyjątków.

-   Stałym powiązaniem punkty przerwania w pewnych zewnętrznej biblioteki dll.

## <a name="12"></a>1.2
 Wydana 2013-03-25

### <a name="new-features"></a>Nowe funkcje

-   Znacznie zwiększona szybkość połączenia debugera.

-   Zoptymalizowane Eksplorator projektu środowiska Unity w większych projektach.

-   Ustawienia programu Visual Studio, aby przerwać (lub nie) uznaje na obsługiwane i nieobsługiwane wyjątki.

-   Uwzględnić ustawienie programu Visual Studio, aby wywołać ToString dla zmiennych lokalnych.

-   Dodaj nowe menu Debuguj -> Dołącz debuger aparatu Unity, które służy do debugowania graczy aparatu Unity.

-   Zachowaj projektach niestandardowych dodawany do rozwiązania UnityVS podczas generowania pliku rozwiązania.

-   Dodawanie nowego skrótu klawiaturowego CTRL + ALT + M -> CTRL + H, aby wyświetlić dokumentację aparatu Unity Unity funkcji lub elementu członkowskiego w położeniu karetki.

-   Kompilator pliki odpowiedzi (rsp) należy wziąć pod uwagę podczas kompilowania w programie Visual Studio.

-   Dekonstruować typów wygenerowanego przez kompilator do wyświetlenia zmiennych podczas debugowania metody generator.

-   Uprość, zdalne debugowanie, usuwając konieczność, aby skonfigurować folder udostępniony do aparatu Unity. Teraz po prostu musisz mieć dostęp do swojego projektu środowiska Unity z Windows.

-   Zainstaluj profil niestandardowy Unity jako profil docelowy .net standard. To naprawia wszystkie fałszywych alarmów, które można pokazać ReSharper.

-   Obejście Unity, skryptów błędów aparatu, aby debuger nie spowodują przerwania działania na innych prawidłowo zarejestrowane wątki.

-   Zmiana zasad użytkownika otwierającego plik, aby uniknąć sytuacji wyścigu, w którym twierdzi mieć możliwość otwarcia plików, podczas awarii na żądanie Otwórz plik w programie VS.

-   UnityVS jest teraz pytaniem odświeżyć kompilacji podczas VS jest kompilowania projektu, a nie w pliku Zapisz dłużej.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono naszych niestandardowego profilu platformy .net

-   Naprawiono integracji motywów, to rozwiązać problemy z naszych z motywu ciemny VS 2012.

-   Naprawiono zachowanie szybkiego skrótu w VS 2012.

-   Rozwiązano problem przechodzenia krok po kroku, który może występować w przypadku debugowania i inne niż główny wątek osiągnie punkt przerwania.

-   Naprawiono uzupełnianie UnityScript i coś, aliasów typu, takie jak int.

-   Naprawiono wyjątek przy pisaniu ciągów UnityScript lub coś nowego.

-   Naprawiono wyjątki w menu Unity, gdy to rozwiązanie nie została załadowana.

-   Usunięto usterkę występującą 48 UV: wpisywanie podwójny cudzysłów czasami generuje błąd i przerwanie wszystkich funkcji (uzupełnianie kodu, wyróżnianie składni itp.).

-   Usunięto usterkę występującą UV 46: Zduplikowany plik otwarty skryptu (UnityScript), po kliknięciu błąd listy z programu Visual Studio.

-   Usunięto usterkę występującą 42 UV: Logo łączność platformy Unity na pasku stanu nie obsługuje zdarzenia myszy w VS 2012.

-   Usunięto usterkę występującą UV 44: CTRL + SHIFT + Q nie jest dostępna w wersji VS 2012 dla szybkich klas Monobehaviour.

-   Usunięto usterkę występującą UV 40: Wybrane elementy w Eksploratorze projektów aparatu Unity były nieczytelne w przypadku, gdy okno jest nieaktywne VS2012 motywu "ciemny".

-   Usunięto usterkę występującą UV 39: Wydać tokenizację ciągów o zmienionym znaczeniu.

-   Usunięto usterkę występującą 35 UV: Wywołaj ToString obiektów, podczas sprawdzania zmiennych.

-   Usunięto usterkę występującą UV 27: Przejdź do symbolu okna sprzeczność z takimi "" ciemny w VS2012.

-   Usunięto usterkę występującą UV-11: Zmienne lokalne w koprocedury.

## <a name="11--beta-release"></a>1.1 — wydanie beta
 Wydana 2014-10-09

## <a name="1013"></a>1.0.13
 Wydana 2013-01-21

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono blokowanie programu Visual Studio, która może się zdarzyć, jeśli obiekt debugowany docelowej wysyła zdarzenia nieprawidłowy wątek. Będzie zazwyczaj mają miejsce podczas debugowania zdalnego aparatu Unity w systemie OSX.

-   Naprawiono blokowanie programu Visual Studio, która może się zdarzyć, jeśli wyjątek zostanie wyłączony debugera.

-   Stała naszych pomocników MonoBehavior, gdy MonoBehavior C# znajduje się w przestrzeni nazw.

-   Ustalonej etykietki narzędzi debugowania dla UnityScript w programie Visual Studio 2012.

-   Naprawiono Generowanie projektu zmiany tylko stałe debugowania z aparatu Unity.

-   Rozwiązany nawigacji za pomocą klawiatury w Eksploratorze projektów aparatu Unity.

-   Kolorowanie UnityScript stałych ciągów o zmienionym znaczeniu.

-   Naprawiono naszych użytkownika otwierającego plik do odgadnięcia lepsze, nazwę projektu, gdy jest używana poza aparatu Unity. Może to być konieczne, gdy użytkownik używa trzeciego użytkownika otwierającego plik części na platformie Unity, który delegował do UnityVS.

-   Naprawiono obsługi długich komunikatów wysyłanych z aparatu Unity do UnityVS. Wcześniej wiadomości długie mogło powodować awarię naszych komunikatów część UnityVS. W konsekwencji czasami UnityVS w takich sytuacjach przydałaby Otwórz plik z poziomu aparatu Unity.

## <a name="1012"></a>1.0.12
 Wydana 2013-01-03

### <a name="bug-fixes"></a>Poprawki błędów

-   Stały blokowanie programu Visual Studio, która może się zdarzyć, gdy program Visual Studio było usunięcie punktu przerwania.

-   Usunięto usterkę, gdzie niektórych punktów przerwania nie będzie trafień, po Unity ponownie kompilowana skrypty gier.

-   Naprawiono debugera, aby prawidłowo powiadamiania programu Visual Studio niepowiązanych zostały punktów przerwania.

-   Rozwiązano problem rejestracji, który może uniemożliwiać debugera programu Visual Studio do debugowania natywnych programów.

-   Naprawiono wyjątek, który może się zdarzyć, gdy oceny UnityScript braz rozruchowy wyrażeń.

-   Naprawiono regresję gdzie zmieniając poziom interfejsu API platformy .net na platformie Unity nie powodowało aktualizację plików projektu.

-   Naprawiono błąd interfejsu API, gdy kod użytkownika nie może uczestniczyć w obsługi wywołania zwrotnego dziennika.

## <a name="1011"></a>1.0.11
 Wydana 28-2012-11

### <a name="new-features"></a>Nowe funkcje

-   Oficjalna Obsługa 4 aparatu Unity.

-   Manipulowanie skryptów w Eksploratorze projektów aparatu Unity.

-   Integracja programu Visual Studio przejdź do okna.

-   Podczas analizowania informacji konsoli wiadomości, więc, że kliknięcie na liście błędów przejście do pierwszego stackframe z symbolami

-   Dodaj [API](../cross-platform/customize-project-files-created-by-vstu.md) aby umożliwić użytkownikowi uczestniczyć w Generowanie projektu.

-   Dodaj [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) aby umożliwić użytkownikowi uczestniczyć w LogCallback.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono Regresje w tle w Eksploratorze projektów aparatu Unity w programie Visual Studio 2012.

-   Naprawiono Generowanie projektu dla użytkowników pełnego profilu platformy .net.

-   Naprawiono Generowanie projektu dla użytkowników w docelowej sieci Web.

-   Generowanie projektu stały obejmujący debugowanie i jest śledzenia symbole kompilacji jako aparatu Unity.

-   Naprawiono awarię przy użyciu znaków specjalnych w naszym okna przejdź do symbolu.

-   Naprawiono awarii, jeśli firma Microsoft nie można wstrzyknąć naszych ikonę na pasku stanu programu Visual Studio.

## <a name="1010"></a>1.0.10
 Wydana 2012-10-09

### <a name="bug-fixes"></a>Poprawki błędów

-   Ustalone tło Eksplorator projektu środowiska Unity w programie Visual Studio 2010.

-   Naprawiono blokowanie programu Visual Studio, która może się zdarzyć, jeśli UnityVS podjęto próbę dołączenia debugera do Unity, którego interfejs debugera wcześniej wystąpiła awaria.

-   Naprawiono blokowanie programu Visual Studio, który może się zdarzyć, gdy ustawiono punkt przerwania i może mieć miejsce, załadowanie obiektu AppDomain.

-   Ustala, jak zestawy są pobierane z aparatu Unity, unikaj blokowania plików i mylić procesu kompilacji aparatu Unity.

## <a name="109"></a>1.0.9
 Wydana 2012-10-03

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono Generowanie projektu, podczas projektu środowiska Unity zawiera rzeczywiste zasoby języka JavaScript.

-   Naprawiono obsługę błędów w Obliczanie wyrażenia.

-   Naprawiono ustawiania nowych wartości do pól typu wartości.

-   Naprawiono możliwe efekty uboczne po najechaniu kursorem na wyrażeniach w edytorze kodu.

-   Ustala, jak typy są przeszukiwane w załadowanych zestawów do obliczenia wyrażenia.

-   Usunięto usterkę występującą UV 21: Ocena przydziału obiektów Unity nie ma znaczenia.

-   Usunięto usterkę występującą UV 21: Nieprawidłowy wskaźnik podczas obliczania wywołanie metody do interfejsu API aparatu Unity matematyczne.

## <a name="108"></a>1.0.8
 Wydana 26-2012-09

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono sposób obiekt otwierający naszego skryptu ścieżkę do projektu, aby być się, że aby znajdował się można otworzyć zarówno w programie Visual Studio, jak i skrypty.

-   Naprawiono usterkę z punktami przerwania utworzone podczas sesji debugowania działał, która może spowodować zablokowanie programu Visual Studio.

-   Ustala, jak UnityVS jest zarejestrowany w programie Visual Studio 2010.

## <a name="107"></a>1.0.7
 Wydana 14-2012-09

### <a name="new-features"></a>Nowe funkcje

-   Visual Studio 2012 pomocy technicznej.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono Generowanie edytora i wtyczek plików projektu, aby dopasować zachowanie mechanizmu Unity.

-   Stałe tłumaczenia symbole .pdb do 4 aparatu Unity.

> [!IMPORTANT]
>  Ze względu na obsługę programu Visual Studio 2012 mieliśmy kilka plików i innych poruszać. Pakiet UnityVS do zaimportowania Unity ma teraz nazwę UnityVS 2010 lub UnityVS 2012 odpowiednio programu Visual Studio 2010 i Visual Studio 2012. Ta wersja wymaga również, że UnityVS pliki projektu są generowane.

## <a name="106---internal-build"></a>1.0.6 — wewnętrzne kompilacji
 Wydana 2012-09-12

## <a name="105"></a>1.0.5
 Wydana 10-2012-09

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono Generowanie plików projektu, gdy skryptów lub programów do cieniowania ma znak nieprawidłowy kod xml.

-   Naprawiono wykrywania wystąpień platformy Unity podczas Unity został połączony z serwerem zawartości. To wyzwalane błędów, aby otworzyć pliki z firm Unity i automatyczne połączenie debugera programu Visual Studio.

## <a name="104"></a>1.0.4
 Wydana 05-2012-09

### <a name="new-features"></a>Nowe funkcje

-   Automatyczna konwersja symbole debugowania na platformie Unity.

     Jeśli masz zestaw .NET DLL za pomocą jego skojarzonego .pdb w folderze zasobów, po prostu ponownie zaimportować zestaw i UnityVS przekonwertuje .pdb w pliku symboli debugowania, rozumie mechanizmu Unity silnik wykonywania skryptów i będzie możliwe do kroku do zestawów .NET z UnityVS.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono UnityVS awarii podczas debugowania spowodowane wyjątki wyrzucane przez metody lub właściwości wewnątrz aparatu Unity.

## <a name="103"></a>1.0.3
 Wydana 2012-09-04

### <a name="new-features"></a>Nowe funkcje

-   Nowa opcja konfiguracji, aby wyłączyć użycie UnityVS umożliwia otwieranie plików z poziomu aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono Generowanie odwołania do UnityEditor edytora innych projektów.

-   Naprawiono definicji symbolu UNITY_EDITOR edytora innych projektów.

-   Naprawiono losowe VS awarii spowodowanych naszych pasek stanu niestandardowych.

## <a name="102"></a>1.0.2
 Wydana 2012-08-30

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono konflikt z debugerem PythonTools.

-   Naprawiono odwołania do Mono.Cecil.

-   Usunięto usterkę występującą w zestawach, jak skrypty zostały pobrane z poziomu aparatu Unity za pomocą aparatu Unity 4 b7.

## <a name="101"></a>1.0.1
 Wydana 28-2012-08

### <a name="new-features"></a>Nowe funkcje

-   Wsparcie dla aparatu Unity 4.0 Beta.

### <a name="bug-fixes"></a>Poprawki błędów

-   Naprawiono kontrolę właściwości zgłaszanie wyjątków.

-   Naprawiono malejąco do obiektów podstawowych, podczas sprawdzania obiektów.

-   Naprawiono puste rozwijanej liście dla punktu wstawiania w Kreatorze MonoBehavior.

-   Naprawiono uzupełnianie dla biblioteki dll znajdujące się w folderze zasobów UnityScript i coś.

## <a name="10--initial-release"></a>Wersji 1.0 — początkowa
 Wydana 22-2012-08
