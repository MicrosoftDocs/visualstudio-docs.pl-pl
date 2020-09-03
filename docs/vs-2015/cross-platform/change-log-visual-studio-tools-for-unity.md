---
title: Dziennik zmian (Visual Studio Tools for Unity) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 751faa1d81ca93fce5f8dfa866327cc8787e27ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825972"
---
# <a name="change-log-visual-studio-tools-for-unity"></a>Dziennik zmian (narzędzia Visual Studio Tools for Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Tools for Unity dziennik zmian.

## <a name="23"></a>2.3

Opublikowano 2016-07-14

### <a name="new-features"></a>Nowe funkcje

- **Główny**

  - Dodano opcję wyłączania dzienników konsoli aparatu Unity na liście błędów programu Visual Studio.

  - Dodano opcję zezwalającą na modyfikowanie wygenerowanych właściwości projektu.

- **Oknie**

  - Dodano Wizualizatory ciągów text, XML, HTML i JSON.

- **Kreatorów**

  - Dodano brakujące działania.

### <a name="bug-fixes"></a>Poprawki błędów

- **Główny**

  - Rozwiązano konflikt z desharper, który uniemożliwił wyświetlanie kontrolek wewnątrz ustawień programu Visual Studio.

  - Rozwiązano konflikt z platformą Xamarin, która uniemożliwiła debugowanie w niektórych przypadkach.

- **Oknie**

  - Rozwiązano problem, który spowodował zablokowanie programu Visual Studio podczas debugowania.

  - Rozwiązano problem z punktami przerwania funkcji w programie Visual Studio 2015.

  - Rozwiązano kilka problemów dotyczących oceny wyrażeń.

## <a name="22"></a>2.2

Opublikowano 2016-02-04

### <a name="new-features"></a>Nowe funkcje

- **Kreatorów**

  - Dodano inteligentne wyszukiwanie w kreatorze **Implementuj działanie** .

  - Zapoznaj się z kontekstem kreatorów; na przykład komunikaty NetworkBehavior są dostępne tylko podczas pracy z NetworkBehavior.

  - Dodano obsługę komunikatów NetworkBehavior w kreatorach.

- **INTERFEJSU użytkownika**

  - Dodano opcję konfigurowania widoczności komunikatów z zachowaniem aktywności.

  - Usunięto strony właściwości programu Visual Studio, które nie są relevent do projektów Unity.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Stałe odwołania do UnityEngine i UnityEditor na platformie Unity 4,6.

  - Stała generacja plików projektu, gdy środowisko Unity działa w systemie OSX.

  - Stała obsługa nazw projektów zawierających znaki HASHMARK (#).

  - Wygenerowane projekty z ograniczeniami do języka C# 4.

- **Oknie**

  - Rozwiązano problem dotyczący obliczania wyrażenia podczas debugowania wewnątrz procedury wspólnej aparatu Unity.

  - Rozwiązano problem, który spowodował zablokowanie programu Visual Studio podczas debugowania.

- **INTERFEJSU użytkownika**

  - Naprawiono niezgodność przy użyciu [kart Studio](https://tabsstudio.com/) Visual Studio Extension.

- **Instalatora**

  - Obsługa instalacji systemu rozszerzenia VSTU (instalacja dla wszystkich użytkowników) przez tworzenie wpisów rejestru HKLM dla całego komputera.

  - Rozwiązano problemy z dezinstalacją rozszerzenia VSTU w przypadku, gdy ta sama wersja programu rozszerzenia VSTU jest zainstalowana dla wielu różnych wersji programu Visual Studio. Na przykład po zainstalowaniu rozszerzenia VSTU **2015** 2.1.0.0 i rozszerzenia VSTU **2013** 2.1.0.0.

## <a name="21"></a>2.1

Opublikowano 2015-09-08

### <a name="new-features"></a>Nowe funkcje

- Obsługa aparatu Unity 5,2

### <a name="bug-fixes"></a>Poprawki błędów

- Elementy menu wyświetlania w aparacie Unity < 4,2

- Komunikat o błędzie nie jest już wyświetlany, gdy program Visual Studio blokuje pliki IntelliSense XML.

- Obsłuż <\<When Changed>> warunkowe punkty przerwania, gdy argument warunkowy nie jest wartością logiczną.

- Stałe odwołania do zestawów UnityEngine i UnityEditor dla aplikacji ze sklepu Windows.

- Naprawiono błąd podczas wykonywania w debugerze: nie można wykonać kroku, ogólny wyjątek.

- Stałe punkty przerwania liczby trafień w programie Visual Studio 2015.

## <a name="20"></a>2,0

Opublikowano 2015-07-20

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja aparatu Unity:**

  - Naprawiono konwersję symboli debugowania utworzonych w programie Visual Studio 2015 podczas importowania biblioteki DLL i jej symboli debugowania (PDB).

  - Zawsze Generuj pliki MDB podczas importowania biblioteki DLL i jej symboli debugowania (PDB), z wyjątkiem sytuacji, gdy plik MDB jest również udostępniony.

  - Stałe zanieczyszczenie katalogu projektu Unity przy użyciu katalogu obj.

  - Stała generacja odwołań do System.Xml. Link i system. Runtime. Serialization.

  - Dodano obsługę wielu subskrybentów do punktów zaczepienia interfejsu API generowania plików projektu.

  - Zawsze kończ generowanie pliku projektu nawet wtedy, gdy jeden z plików do wygenerowania jest zablokowany.

  - Dodano obsługę symboli wieloznacznych * w filtrze rozszerzeń podczas określania plików, które mają być zawarte w projekcie języka C#.

- **Integracja z programem Visual Studio:**

  - Rozwiązano problem ze zgodnością z narzędziami do wydajnej pracy.

  - Naprawiono generowanie biozachowań wokół zdarzeń i deklaracji delegatów.

- **Oknie**

  - Naprawiono potencjalne Zawieszanie podczas debugowania.

  - Rozwiązano problem polegający na tym, że lokalne nie będą wyświetlane w określonych ramkach stosu.

  - Naprawiono inspekcję pustych tablic.

## <a name="20-preview-2"></a>2,0 wersja zapoznawcza 2
Opublikowano 2015-04-02

### <a name="new-features"></a>Nowe funkcje

- **Eksplorator projektów aparatu Unity:**

  - Automatycznie Zmień nazwę klasy podczas zmiany nazwy pliku w Eksploratorze projektów aparatu Unity (Zobacz okno dialogowe **opcji** ).

  - Automatycznie wybierz nowo utworzone skrypty w Eksploratorze projektów aparatu Unity.

  - Śledź aktywny skrypt w Eksploratorze projektów aparatu Unity (Zobacz okno dialogowe **opcji** ).

  - Podwójna synchronizacja Eksplorator rozwiązań programu Visual Studio (Zobacz okno dialogowe **opcji** ).

  - Zastosuj ikony programu Visual Studio w Eksploratorze projektów aparatu Unity.

- **Oknie**

  - Wybierz aktywny obiekt docelowy debugowania z listy zapisanych lub ostatnio używanych elementów docelowych debugowania (Zobacz okno dialogowe **opcji** ).

  - Tworzenie punktów przerwania funkcji w metodach o postaci jednopolowej i stosowanie ich do wielu klas zachowań.

  - Obsługa popełniania identyfikatora obiektu w debugerze.

  - Obsługa liczby trafień punktu przerwania w debugerze.

  - Obsługa wyjątku przerwy w debugerze (wersja eksperymentalna). Zobacz okno dialogowe **Opcje** .

  - Obsługa tworzenia obiektów i tablic podczas oceniania wyrażeń w debugerze.

  - Obsługa porównania wartości null w przypadku wyrażeń oceny w debugerze.

  - Odfiltruj przestarzałe elementy członkowskie w oknach czujka debugera.

- **Instalatora**

  - Zoptymalizowano rejestrację rozszerzenia Visual Studio Tools for Unity.

  - Zainstaluj pakiet Visual Studio Tools for Unity dla aparatu Unity 5.

- **Dokumentacja:** Poprawa wydajności generowania dokumentacji.

- **Kreatorzy:** Obsługa nowych metod antyzachowań dla aparatu Unity 4,6 i aparatu Unity 5.

- **Środowisko Unity:** Wyszukiwanie niebezpiecznych flag i niestandardowych definiuje w plikach. rsp podczas generowania pliku projektu.

- **Interfejs użytkownika:** Dodano okno dialogowe **opcji** Visual Studio Tools for Unity w programie Visual Studio.

### <a name="bug-fixes"></a>Poprawki błędów

- **Eksplorator projektów aparatu Unity:**

  - Odśwież Eksplorator projektów środowiska Unity po przeniesieniu plików lub zmianie ich nazwy z Eksplorator rozwiązań programu Visual Studio.

  - Zachowaj wybory podczas zmieniania nazw plików w Eksploratorze projektów aparatu Unity.

  - Zapobiegaj automatycznemu rozwijaniu i zwijaniu po dwukrotnym kliknięciu plików w Eksploratorze projektów aparatu Unity.

  - Upewnij się, że nowo wybrane pliki są widoczne w Eksploratorze projektów aparatu Unity.

- **Oknie**

  - Zapobiegaj możliwemu zablokowaniu programu Visual Studio podczas oceniania wyrażeń w debugerze.

  - Upewnij się, że wywołania metody są wykonywane w odpowiedniej domenie w debugerze.

- **Unity**

  - Popraw lokalizację UnityVS. OpenFile z aparatem Unity 5.

  - Popraw lokalizację pdb2mdb za pomocą aparatu Unity 5.

  - Zapobiegaj możliwemu wystąpieniu wyjątku podczas generowania pliku projektu.

  - Zapobiegaj możliwemu zablokowaniu podczas korzystania z aparatu Unity w systemie OSX.

  - Obsługa wyjątków wewnętrznych.

  - Wyślij dzienniki konsoli aparatu Unity do listy błędów programu VS.

- **Dokumentacja:** Poprawna generacja dokumentacji dotycząca nowej dokumentacji aparatu Unity.

- **Projekt:** Przenieś i Zmień nazwę plików Unity. meta w razie konieczności, nawet w folderach.

- **Kreatorzy:** Popraw kolejność parametrów metody z zachowaniem wartości podczas generowania kodu.

- **Interfejs użytkownika:** Obsługuj motywy programu Visual Studio dla menu kontekstowego i ikon.

## <a name="20-preview"></a>wersja zapoznawcza 2,0
Opublikowano 2014-11-12

### <a name="new-features"></a>Nowe funkcje

- Obsługa programu Visual Studio 2015.

- Zabarwienie kodu dla programów do cieniowania aparatu Unity w programie Visual Studio 2015.

- Ulepszona Wizualizacja wartości podczas debugowania:

  - Lepsza Wizualizacja dla niezsynchronizowane listy ArrayLists, list, tablic skrótów i słowników.

  - Pokaż niepubliczne składowe i statyczne elementy członkowskie jako Kategorie w widokach czujki i lokalne.

  - Ulepszono wyświetlanie SerializedProperty środowiska Unity w celu obliczenia tylko pola wartości poprawnego dla właściwości.

  - Obsługa DebuggerDisplayAttribute — dla klas i struktur.

  - Obsługa DebuggerTypeProxyAttribute —.

- Wstaw metody z zastosowaniem zachowań przy użyciu naszych kreatorów, aby przestrzegać konwencji kodowania użytkownika.

- Zaimplementuj obsługę szablonów tekstu w czasie kompilacji w projektach UnityVS wygenerowanych.

- Zaimplementuj obsługę zasobów ResX w projektach UnityVS wygenerowanych.

- Obsługa otwierania programów do cieniowania w programie Visual Studio z aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

- Wyczyszczenie gniazd przed rozpoczęciem gry w aparacie Unity po wyzwoleniu Attach i Play w programie Visual Studio. Rozwiązuje to pewne problemy ze stabilnością połączenia między środowiskiem Unity a programem VS przy użyciu funkcji Attach i Play.

- Unikaj wywoływania metod w interfejsie debugera aparatu skryptów aparatu Unity, które są podatne na zablokowanie aparatu Unity. Powoduje to rozwiązanie aparatu Unity podczas dołączania debugera.

- Naprawianie wyświetlania elementu stosy wywołań, gdy nie ma dostępnych symboli.

- Nie Rejestruj wywołania zwrotnego dziennika, jeśli nie jest to konieczne.

## <a name="192"></a>1.9.2

Opublikowano 2014-10-09

### <a name="new-features"></a>Nowe funkcje

- Ulepszanie wykrywania graczy aparatu Unity.

- W przypadku korzystania z naszego narzędzia do otwierania plików w środowisku Unity należy przekazać numer wiersza oraz nazwę pliku.

- Domyślna dokumentacja środowiska Unity w trybie online, jeśli nie istnieje lokalna dokumentacja.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawianie potencjalnej awarii aparatu Unity po ponownym załadowaniu domeny do punktu przerwania.

- Po ponownym załadowaniu domeny usuń wyjątki wyświetlane w konsoli aparatu Unity.

- Rozwiązywanie problemów z wykrywaniem środowiska 64bits Unity działającego lokalnie.

- Poprawianie filtrowania zachowań jednowartościowych na wersję aparatu Unity w kreatorach.

- Usuń usterkę, w której wszystkie zasoby zostały uwzględnione w plikach projektu, jeśli filtr rozszerzenia był pusty.

## <a name="191"></a>1.9.1

Opublikowano 2014-09-22

### <a name="new-features"></a>Nowe funkcje

- Zoptymalizuj punkt przerwania powiązania z lokalizacjami źródłowymi.

- Obsługa przeciążonych metod podczas obliczania wyrażenia debugera.

- Obsługa elementów podstawowych i typów wartości opakowania w ocenie wyrażenia debugera.

- Obsługa ponownego tworzenia środowiska zmiennych lokalnych języka C# podczas debugowania metod anonimowych.

- Usuń pliki i zmień ich nazwy podczas usuwania lub zmiany nazwy plików z programu Visual Studio.

### <a name="bug-fixes"></a>Poprawki błędów

- Rozwiązywanie problemów z obsługą motywów programu Visual Studio. Wcześniej okna dialogowe z czarnym kompozycjami mogą być puste.

- Naprawianie aparatu Unity podczas nawiązywania połączenia z debugerem podczas ponownej kompilacji aparatu Unity.

- Naprawianie punktów przerwania podczas debugowania zdalnych edytorów lub graczy skompilowanych w innym systemie.

- Naprawianie możliwej awarii programu Visual Studio po trafieniu punktu przerwania.

- Naprawianie powiązań punktów przerwania, aby uniknąć punktów przerwania pokazywanych jako zwolnione.

- Napraw obsługę zakresu zmiennej w debugerze, aby uniknąć aktywnych zmiennych, które znajdują się poza zakresem.

- Popraw wyszukiwanie statycznych elementów członkowskich w ocenie wyrażenia debugera.

- Popraw wyświetlanie typów w ocenie wyrażenia debugera, aby wyświetlić statyczne pola i właściwości.

- Napraw generowanie rozwiązania, gdy nazwy projektów aparatu Unity zawierają znaki specjalne, które program Visual Studio zabroni (#948666 problemu).

- Napraw pakiet Visual Studio Tools Unity, aby natychmiast zatrzymać wysyłanie zdarzeń konsoli po usunięciu zaznaczenia opcji (Nawiąż problemy #933357).

- Rozwiązywanie problemów z wykrywaniem w celu prawidłowego ponownego wygenerowania odwołań do nowych interfejsów API, takich jak UnityEngine. UI w projektach UnityVS Generate.

- Napraw Instalatora, aby wymagać zamknięcia programu Visual Studio przed instalacją w celu uniknięcia uszkodzonych instalacji.

- Napraw Instalatora, aby zainstalować zestawy referencyjne aparatu Unity jako prawidłowy składnik autonomiczny współużytkowany przez wszystkie wersje programu rozszerzenia VSTU.

- Napraw otwieranie skryptów z rozszerzenia VSTU w wersji 64 usługi Unity.

## <a name="19"></a>1,9

Opublikowano 2014-07-29

### <a name="new-features"></a>Nowe funkcje

- W oknie Dołącz debuger aparatu Unity Dodaj możliwość wprowadzenia niestandardowego adresu IP i portu do debugowania.

- Dodaj opcję konfiguracji, aby ustawić środowisko Unity do uruchamiania w tle.

- Dodaj opcję konfiguracji, aby wygenerować tylko pliki rozwiązania i projektu lub pliki projektu.

- Obiekt docelowy uruchamiania: wybierz opcję dołączenia do aparatu Unity lub Dołącz do aparatu Unity i Odtwórz.

- Wyświetlanie wielowymiarowych tablic w debugerze.

- Obsługa nowych portów debugowania odtwarzacza Unity.

- Dojście do dojścia do nowych zestawów Unity, takich jak zestawy GUI 4,6 dla aparatu Unity.

- Dekonstrukcjauje zamknięcia, aby prawidłowo wyświetlać zmienne lokalne podczas debugowania.

- Dekonstrukcjauje wygenerowane zmienne iteratorów do argumentów podczas debugowania.

- Zachowaj stan Eksploratora projektów aparatu Unity po załadowaniu projektu.

- Dodaj polecenie, aby zsynchronizować Eksplorator projektów środowiska Unity z bieżącym dokumentem.

### <a name="bug-fixes"></a>Poprawki błędów

- Usuń warunkowe punkty przerwania, których warunki są ustawione przed rozpoczęciem debugera.

- Napraw odwołania do UnityEngine, aby uniknąć ostrzeżeń.

- Popraw wersje analizy dla wersji beta środowiska Unity.

- Rozwiąż problem, gdy zmienne nie będą wyświetlane w oknie zmiennych lokalnych podczas przechodzenia do punktu przerwania.

- Popraw zmienne etykietki narzędzi w Visual Studio 2013.

- Napraw generację dokumentacji IntelliSense dla aparatu Unity 4,5.

- Naprawianie komunikacji aparatu Unity/programu Visual Studio po ponownym załadowaniu domeny (Odtwórz/Zatrzymaj w aparacie Unity).

- Rozwiązywanie problemów z obsługą części motywów programu Visual Studio.

> [!IMPORTANT]
> C# jest językiem przeważanym w ekosystemie Unity — nowe przykładowe zasoby znajdują się w języku C#, a dokumentacja aparatu Unity będzie domyślnie w języku C# — usunęliśmy podstawową pomoc techniczną dla UnityScript i Boo w celu lepszego skoncentrowania się na środowisku C#. W związku z tym rozwiązania rozszerzenia VSTU są teraz tylko w języku C# i są znacznie szybsze.

## <a name="182"></a>1.8.2

Opublikowano 2014-01-07

### <a name="new-features"></a>Nowe funkcje

- Obejście problemu w warstwie sieciowej aparatu skryptów środowiska Unity w Mavericks na potrzeby zdalnego odnajdywania edytorów.

- Obsługa nowych portów w celu odnajdywania zdalnych odtwarzaczy Unity.

- Odwołuje się do zestawu UnityEngine, który jest specyficzny dla bieżącego celu kompilacji.

- Dodaj ustawienie, aby filtrować pliki do uwzględnienia w wygenerowanych projektach.

- Dodaj ustawienie, aby wyłączyć wysyłanie dzienników konsoli do listy błędów programu Visual Studio. Jest to przydatne, jeśli korzystasz z programu PlayMaker lub konsoli Pro, ponieważ w aparacie Unity może być zarejestrowane tylko jedno wywołanie zwrotne do odbierania dzienników konsoli.

- Dodaj ustawienie, aby wyłączyć generowanie symboli debugowania mdb. Jest to przydatne, jeśli samodzielnie generujesz mdb.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawianie regresji, gdy pliki otwierane w programie VS z aparatu Unity >= 4,2 spowoduje utratę technologii IntelliSense.

- Popraw nasze okna dialogowe programu VS, aby obsługiwać niestandardowe motywy.

- Poprawka zamykająca menu kontekstowe UPE.

- Zapobiegaj awariom w środowisku Unity, gdy zestaw wygenerował specyficzną wersję, jeśli nie jest zsynchronizowany.

## <a name="181"></a>1.8.1

Opublikowano 2013-11-21

### <a name="new-features"></a>Nowe funkcje

- Wyregulowano kreatorów z niedziałami przy użyciu interfejsów API aparatu Unity 4,3.

- Kreatory z zastosowaniem zachowań umożliwiają filtrowanie interfejsów API Unity w zależności od używanej wersji.

- Dodaj odwołanie do System.Xml. LINQ do projektów dla aparatu Unity > 4,1.

- Prettify nasze wywołania do debugowania. log, aby nie zawierały początku ślad stosu w komunikacie.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono usterkę, w której będziemy przeszkadzać w domyślnej obsłudze plików JavaScript w programie Visual Studio.

- W tym czasie Naprawiono biały piksel w programie VS.

- Naprawiono usunięcie zestawu UnityVS. VersionSpecific, jeśli jest oznaczony jako tylko do odczytu przez menedżera SCM.

- Rozwiązano wyjątki podczas tworzenia gniazd w pakiecie UnityVS.

- Naprawiono awarię w programie Visual Studio podczas ładowania obrazów podstawowych z zestawów programu Visual Studio.

- Rozwiązano błąd w generacji UnityVS. VersionSpecific dla kompilacji źródłowej aparatu Unity.

- Rozwiązano możliwe zablokowanie podczas otwierania gniazda w pakiecie Unity.

- Naprawiono obsługę projektu Unity z kreską (-) w nazwie.

- Naprawiono otwieranie skryptów z aparatu Unity, aby nie mylić kolejności klawiszy ALT + TAB dla aparatu Unity 4,2 i nowszych.

## <a name="180"></a>1.8.0

Opublikowano 2013-09-24

### <a name="new-features"></a>Nowe funkcje

- Drastycznie ulepszona szybkość połączenia debugera.

- Automatycznie Obsługuj nawigację do pliku i wiersza w aparacie Unity 4,2 i nowszych.

- Warunkowe punkty przerwania.

- Generator plików projektu obsługuje teraz szablony T4.

- Aktualizowanie kreatorów MonBehavior za pomocą nowych interfejsów API.

- Dokumentacja technologii IntelliSense w języku C# dla typów Unity.

- Obliczanie wyrażeń arytmetycznych i logicznych.

- Lepsze odnajdowanie zdalnych edytorów w podglądzie zdalnego debugowania.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono usterkę, w której będziemy wyciekać wątek w programie VS po rozłączeniu debugera.

- Naprawiono biały piksel pojawiający się w programie VS.

- Naprawiono obsługę kliknięć na ikonie paska stanu.

- Rozwiązano generowanie odwołań z zestawami w folderach wtyczek.

- Naprawiono tworzenie gniazd z pakietu UnityVS w przypadku wyjątków.

- Rozwiązano wykrywanie nowych wersji programu UnityVS.

- Naprawiono monit Menedżera licencji, gdy licencja wygasła.

- Rozwiązano błąd, który może renderować pustą listę procesów w debugerze Dołącz do przetworzenia okna programu VS.

- Naprawiono zmiany wartości logicznych w widoku lokalnym.

## <a name="122"></a>ppkt

Opublikowano 2013-07-09

### <a name="bug-fixes"></a>Poprawki błędów

- Obsługa w pełni kwalifikowanych nazw w ewaluatora wyrażeń.

- Naprawiono zamrożenie związane z obsługą wyjątków, gdzie aparat skryptów Unity wysyła nam nieprawidłowe dane StackFrame.

- Stały proces kompilacji dla obiektów docelowych sieci Web.

- Rozwiązano błąd, który może wystąpić, jeśli program Visual Studio został uruchomiony i że usunięty plik znajdował się na liście plików do otwarcia podczas uruchamiania.

- Rozwiązano UnityVS. OpenFile do obsługi plików nieskryptowych, takich jak skompilowane programy do cieniowania.

- Teraz odwołujemy się do boo. lang i UnityScript. lang ze wszystkich projektów w języku C#.

- Stałe generowanie odwołań w projektach, jeśli projekt zawiera znaki specjalne.

- Obejście problemu VS, gdy metoda wywołuje do usuniętych projektów wywoła wiele NullReferenceException MessageBox.

- Stała Obsługa zestawów systemu Unity 4,2 beta.

## <a name="121"></a>1.2.1

Opublikowano 2013-04-09

### <a name="bug-fixes"></a>Poprawki błędów

- Stałe lokalne wdrożenie zestawów Unity do uzupełniania kodu w przypadku błędu we/wy (na przykład plików tylko do odczytu lub plików zablokowanych przez program Visual Studio).

- Naprawiono regresję, w której otwieranie skryptu z aparatu Unity nie spowoduje skoncentrowania się na pliku, jeśli został on już otwarty w programie Visual Studio.

- Rozwiązano problem z wydajnością nowej obsługi wyjątków.

- Stałe powiązania punktów przerwania w niektórych zewnętrznych bibliotekach DLL.

## <a name="12"></a>1,2

Opublikowano 2013-03-25

### <a name="new-features"></a>Nowe funkcje

- Drastycznie ulepszona szybkość połączenia debugera.

- Zoptymalizowany Eksplorator projektów środowiska Unity dla większych projektów.

- Należy przestrzegać ustawień programu Visual Studio, aby przerwać (lub nie) w przypadku obsłużonych i nieobsłużonych wyjątków.

- Należy przestrzegać ustawienia programu Visual Studio, aby wywołać metodę ToString dla zmiennych lokalnych.

- Dodaj nowe menu Debuguj-> Dołącz debuger Unity, którego można użyć do debugowania graczy aparatu Unity.

- Zachowaj niestandardowe projekty dodane do rozwiązania UnityVS podczas generowania pliku rozwiązania.

- Dodaj nowy skrót klawiaturowy CTRL + ALT + M-> CTRL + H, aby wyświetlić dokumentację aparatu Unity dla funkcji lub składowej aparatu Unity w położeniu karetki.

- Należy wziąć pod uwagę pliki odpowiedzi kompilatora (RSP) podczas kompilowania z programu Visual Studio.

- Dekonstrukcja typów generowanych przez kompilator, aby pokazać zmienne podczas debugowania metod generatora.

- Uprość debugowanie zdalne, usuwając konieczność skonfigurowania folderu udostępnionego do aparatu Unity. Teraz wystarczy mieć dostęp do projektu Unity z systemu Windows.

- Zainstaluj niestandardowy profil aparatu Unity jako standardowy profil docelowy platformy .NET. Spowoduje to usunięcie wszystkich fałszywych wartości dodatnich, które mogą być wyświetlane przez program.

- Obejście błędu aparatu skryptów aparatu Unity, dzięki czemu debuger nie będzie przerywał pracy w niewłaściwie zarejestrowanych wątkach.

- Należy ponownie uruchomić program do otwierania plików, aby uniknąć sytuacji wyścigu w programie VS, gdy zażądano otwarcia plików, podczas gdy żądanie otwarcia pliku zostało zakończone.

- UnityVS prosi teraz o odświeżenie kompilacji podczas kompilowania projektu, a nie zapisywania w pliku.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono nasz niestandardowy profil platformy .NET

- Naprawiono integrację z motywem, dzięki czemu Rozwiązywanie problemów z ciemną kompozycją VS 2012.

- Naprawiono skrót szybkiego zachowania w programie VS 2012.

- Rozwiązano problem z taktem, który może wystąpić, gdy debugowanie i wątek niebędący w wątku niegłównym trafią na punkt przerwania.

- Stałe UnityScript i Booe ukończenie aliasów typu, takich jak int.

- Naprawiono wyjątek podczas zapisywania nowego ciągu UnityScript lub boo.

- Stałe wyjątki w menu aparatu Unity, gdy rozwiązanie nie zostało załadowane.

- Naprawiono usterkę UVS-48: wpisanie podwójnego cudzysłowu czasami powoduje błąd i przerwanie wszystkich funkcji (uzupełnianie kodu, wyróżnianie składni itp.).

- Naprawiono usterkę UVS-46: zduplikowany otwarty plik skryptu (UnityScript) podczas klikania Lista błędów programu Visual Studio.

- Naprawiono usterkę UVS-42: logo łączności Unity na pasku stanu nie obsługuje zdarzeń myszy w programie VS 2012.

- Naprawiono usterkę UVS-44: CTRL + SHIFT + Q nie jest dostępna w programie VS 2012 w przypadku szybkich zachowań.

- Naprawiono usterkę UVS-40: wybrane elementy w Eksploratorze projektów aparatu Unity nie są czytelne, gdy okno jest nieaktywne w motywie VS2012 "ciemny".

- Naprawiono usterkę UVS-39: wydaj tokenizowanie ciągi ucieczki.

- Naprawiono usterkę UVS-35: Wywołaj ToString dla obiektów podczas inspekcji zmiennych.

- Naprawiono usterkę UVS-27: Przejdź do okna symboli niespójności z motywem "ciemny" w VS2012.

- Naprawiono usterkę UVS-11: locale w procedurach wspólnych.

## <a name="11--beta-release"></a>1,1 — wydanie beta
Opublikowano 2014-10-09

## <a name="1013"></a>1.0.13
Opublikowano 2013-01-21

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono blokowanie programu Visual Studio, które może się zdarzyć, jeśli element docelowy debugowanego obiektu wysyła nieprawidłowe zdarzenia wątku. Zwykle jest to spowodowane debugowaniem zdalnego aparatu Unity w systemie OSX.

- Naprawiono blokowanie programu Visual Studio, które może się zdarzyć, jeśli wyjątek zamyka debuger.

- Naprawiono nasze pomocników z pomocą techniczną, gdy w przestrzeni nazw znajduje się funkcja bezproblemowa w języku C#.

- Stałe etykietki narzędzi debugera dla UnityScript w programie Visual Studio 2012.

- Stała generacja projektu, gdy tylko stałe debugowania są zmieniane z aparatu Unity.

- Stałe nawigowanie po klawiaturze w Eksploratorze projektów aparatu Unity.

- Stałe kolorowanie UnityScript dla ciągów z ucieczką.

- Naprawiono nasz plik do odgadnięcia, aby lepiej wykorzystać nazwę projektu, gdy jest on używany poza środowiskiem Unity. Jest to konieczne, gdy użytkownik korzysta z otwartego pliku częściowego, który deleguje do UnityVS.

- Stała obsługa długich komunikatów wysyłanych z aparatu Unity do UnityVS. Wcześniej długi komunikat może ulec awarii naszej części komunikatów UnityVS. W związku z tym czasami UnityVS otworzyć plik z aparatu Unity.

## <a name="1012"></a>1.0.12
Opublikowano 2013-01-03

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono blokowanie programu Visual Studio, które mogło się zdarzyć, gdy program Visual Studio usunie punkt przerwania.

- Rozwiązano problem polegający na tym, że niektóre punkty przerwania nie zostaną trafione po ponownym skompilowaniu skryptów aparatu Unity.

- Rozwiązano debuger, aby prawidłowo powiadamiał program Visual Studio, gdy punkty przerwania zostały anulowane.

- Rozwiązano problem z rejestracją, który może uniemożliwić debugerowi programu Visual Studio debugowanie programów natywnych.

- Rozwiązano wyjątek, który może wystąpić podczas oceny wyrażeń UnityScript i boo.

- Naprawiono regresję, w której zmiana poziomu interfejsu API platformy .NET w aparacie Unity nie spowoduje wyzwolenia aktualizacji plików projektu.

- Naprawiono błąd interfejsu API, gdzie kod użytkownika nie może uczestniczyć w obsłudze wywołania zwrotnego dziennika.

## <a name="1011"></a>1.0.11
Opublikowano 2012-11-28

### <a name="new-features"></a>Nowe funkcje

- Oficjalne wsparcie dla aparatu Unity 4.

- Manipulowanie skryptami z Eksploratora projektów środowiska Unity.

- Integracja w programie Visual Studio — przejdź do okna.

- Analizowanie komunikatu konsoli informacyjnej, aby kliknięcie w Lista błędów do pierwszej StackFrame z symbolami.

- Dodaj [interfejs API](../cross-platform/customize-project-files-created-by-vstu.md) , aby umożliwić użytkownikowi uczestnictwo w generowaniu projektu.

- Dodaj [interfejs API](../cross-platform/share-the-unity-log-callback-with-vstu.md) , aby umożliwić użytkownikom uczestnictwo w LogCallback.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono regresję w tle Eksploratora projektów aparatu Unity w programie Visual Studio 2012.

- Stała generacja projektu dla użytkowników pełnego profilu platformy .NET.

- Stała generacja projektu dla użytkowników obiektu docelowego sieci Web.

- Stała generacja projektu obejmująca symbole kompilacji debugowania i śledzenia jako aparat Unity.

- Naprawiono awarię w przypadku używania znaków specjalnych w naszym oknie symbolu przejdź do.

- Naprawiono awarię, jeśli nie możemy wstrzyknąć naszej ikony na pasku stanu programu Visual Studio.

## <a name="1010"></a>1.0.10
Opublikowano 2012-10-09

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono tło Eksploratora projektów aparatu Unity w programie Visual Studio 2010.

- Rozwiązano blokadę programu Visual Studio, która może wystąpić, jeśli UnityVS próbował podłączyć debuger do aparatu Unity, którego interfejs debugera wcześniej uległ awarii.

- Naprawiono zablokowanie programu Visual Studio, który może mieć miejsce, gdy punkt przerwania został ustawiony i wystąpił ponowny ładowanie elementu AppDomain.

- Ustalono, jak zestawy są pobierane z aparatu Unity, aby uniknąć zablokowania plików i pomylić proces kompilacji aparatu Unity.

## <a name="109"></a>1.0.9

Opublikowano 2012-10-03

### <a name="bug-fixes"></a>Poprawki błędów

- Stała generacja projektu, gdy projekt Unity zawiera rzeczywiste zasoby JavaScript.

- Naprawiono obsługę błędów podczas obliczania wyrażenia.

- Naprawiono nowe wartości dla pól typu wartości.

- Stałe możliwe efekty uboczne po umieszczeniu wskaźnika myszy na wyrażeniach z edytora kodu.

- Naprawiono sposób, w jaki typy są przeszukiwane w załadowanych zestawach do oceny wyrażenia.

- Stała usterka UVS-21: Obliczanie przydziału obiektów Unity nie ma żadnego wpływu.

- Naprawiono usterkę UVS-21: nieprawidłowy wskaźnik podczas oceniania wywołania metody do interfejsu API Math aparatu Unity.

## <a name="108"></a>1.0.8

Opublikowano 2012-09-26

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono sposób, w jaki nasz program do otwierania skryptów uzyskał ścieżkę do projektu, aby upewnić się, że jest w stanie otworzyć zarówno program Visual Studio, jak i skrypty.

- Naprawiono usterkę z punktami przerwania utworzonymi podczas działania sesji debugowania, która może spowodować zablokowanie programu Visual Studio.

- Ustalono, jak UnityVS jest zarejestrowany w programie Visual Studio 2010.

## <a name="107"></a>1.0.7

Opublikowano 2012-09-14

### <a name="new-features"></a>Nowe funkcje

- Obsługa programu Visual Studio 2012.

### <a name="bug-fixes"></a>Poprawki błędów

- Stała generacja plików projektu edytora i wtyczek, aby dopasować zachowanie aparatu Unity.

- Naprawiono tłumaczenie symboli. pdb w aparacie Unity 4.

> [!IMPORTANT]
> Ze względu na pomoc techniczną dla programu Visual Studio 2012 należy zmienić nazwę kilku plików i przenieść inne. Pakiet UnityVS do zaimportowania aparatu Unity ma teraz nazwę UnityVS 2010 lub UnityVS 2012 dla odpowiednio programu Visual Studio 2010 i Visual Studio 2012. Ta wersja wymaga również ponownego wygenerowania plików projektu UnityVS.

## <a name="106---internal-build"></a>1.0.6 — kompilacja wewnętrzna
Opublikowano 2012-09-12

## <a name="105"></a>1.0.5

Opublikowano 2012-09-10

### <a name="bug-fixes"></a>Poprawki błędów

- Stała generacja plików projektu, gdy skrypty lub cieniowanie mają nieprawidłowy znak XML.

- Stałe wykrywanie wystąpień aparatu Unity, gdy środowisko Unity zostało połączone z serwerem zasobów. Wyzwolone błędy otwierania plików z aparatu Unity i automatycznego połączenia debugera programu Visual Studio.

## <a name="104"></a>1.0.4

Opublikowano 2012-09-05

### <a name="new-features"></a>Nowe funkcje

- Automatyczna konwersja symboli debugowania w środowisku Unity.

    Jeśli masz zestaw .NET. dll ze skojarzonym z nim plikiem. pdb w folderze Asset, po prostu zaimportuj zestaw i UnityVS przekonwertujemy plik. pdb do pliku symboli debugowania, który jest rozpoznawany przez aparat skryptów aparatu Unity, i będzie można przejść do zestawów .NET z UnityVS.

### <a name="bug-fixes"></a>Poprawki błędów

- Stała awaria UnityVS podczas debugowania spowodowana przez wyjątki zgłoszone przez metody lub właściwości wewnątrz aparatu Unity.

## <a name="103"></a>1.0.3

Opublikowano 2012-09-04

### <a name="new-features"></a>Nowe funkcje

- Nowa opcja konfiguracji, aby wyłączyć użycie UnityVS do otwierania plików z aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

- Stałe generowanie odwołań do UnityEditor dla projektów bez edytora.

- Stała definicja symbolu UNITY_EDITOR dla projektów nie będących edytorami.

- Naprawiono losowy program VS Crash z powodu niestandardowego paska stanu.

## <a name="102"></a>1.0.2

Opublikowano 2012-08-30

### <a name="bug-fixes"></a>Poprawki błędów

- Rozwiązano konflikt z debugerem PythonTools.

- Stałe odwołania do mono. Cecil.

- Rozwiązano problem polegający na tym, jak zestawy skryptów zostały pobrane z aparatu Unity z aparatu Unity 4 B7.

## <a name="101"></a>1.0.1

Opublikowano 2012-08-28

### <a name="new-features"></a>Nowe funkcje

- Obsługa wersji zapoznawczej dla aparatu Unity 4,0 beta.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono inspekcję właściwości zgłaszających wyjątki.

- Naprawiono malejąco na podstawie obiektów podstawowych podczas przeprowadzania inspekcji obiektów.

- Usunięto pustą listę rozwijaną dla punktu wstawiania w Kreatorze działania.

- Naprawiono uzupełnianie dla biblioteki DLL wewnątrz folderu zasobów dla UnityScript i boo.

## <a name="10--initial-release"></a>1,0 — wersja początkowa
Opublikowano 2012-08-22
