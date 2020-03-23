---
title: Dziennik zmian (Narzędzia programu Visual Studio dla unity, Windows) | Dokumenty firmy Microsoft
ms.custom: ''
ms.date: 12/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 0e1810f452f48c95e0c4e8117820be3598b0f139
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74706783"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Dziennik zmian (Visual Studio Tools for Unity, Windows)

Visual Studio Narzędzia dla dziennika zmian Unity.

## <a name="4420"></a>4.4.2.0

Wydano 3 grudnia 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Poprawiono diagnostykę z interfejsami zdefiniowanymi przez użytkownika.

  - Naprawiono szybkie etykietki narzędzi z zniekształconych wyrażeń.

## <a name="4410"></a>4.4.1.0

Wydano 6 listopada 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę procesów w tle Unity. (Debuger jest w stanie automatycznie połączyć się z procesem głównym zamiast procesu podrzędnego).
  
  - Dodano szybką etykietkę narzędzia dla komunikatów Unity, wyświetlającą skojarzoną dokumentację.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono analizator `UNT0002` porównywania tagów z zaawansowanymi wyrażeniami binarnymi i wywołanymi.

### <a name="deprecated-features"></a>Przestarzałe funkcje

- **Integracji:**

  - W przyszłości narzędzia programu Visual Studio dla unity będą obsługiwać tylko program Visual Studio 2017+.

## <a name="4400"></a>4.4.0.0

Wydano 15 października 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano tłumik `IDE0060` dla (nieużywany parametr) dla wszystkich komunikatów Unity.
  
  - Dodano szybką etykietkę narzędzia dla `TooltipAttribute`pól oznaczonych tagiem . (To będzie działać na prosty uzyskać akcesor za pomocą tego pola, jak również).

## <a name="4330"></a>4.3.3.0

Wydano 23 września 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono raportowanie błędów i ostrzeżeń dla lekkich kompilacji.

## <a name="4320"></a>4.3.2.0

Wydano 16 września 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Pogłębiliśmy zrozumienie, że visual studio ma dla projektów Unity, dodając nowe diagnostyki specyficzne dla Unity. Wprowadziliśmy również zmiany powodujące, że środowisko IDE działa teraz bardziej inteligentnie dzięki pomijaniu ogólnej diagnostyki języka C#, która nie dotyczy projektów Unity. Na przykład IDE nie będzie wyświetlać quick-fix, aby `readonly` zmienić zmienną inspektora, do którego uniemożliwiłoby modyfikowanie zmiennej w Edytorze Unity.
    - `UNT0001`: Unity komunikaty są wywoływane przez środowisko wykonawcze, nawet jeśli są one puste, nie deklaruj ich, aby uniknąć uncesseray przetwarzania przez środowisko uruchomieniowe Unity.
    - `UNT0002`: Porównanie znaczników przy użyciu równości ciągów jest wolniejsze niż wbudowana metoda CompareTag.
    - `UNT0003`: Użycie ogólnej formy GetComponent jest preferowane dla bezpieczeństwa typu.
    - `UNT0004`: Aktualizacja wiadomości jest zależna od szybkości klatek i powinna używać Time.deltaTime zamiast Time.fixedDeltaTime.
    - `UNT0005`: Komunikat FixedUpdate jest niezależny od szybkości klatek i powinien używać Time.fixedDeltaTime zamiast Time.deltaTime.
    - `UNT0006`: Wykryto niepoprawny podpis metody dla tej wiadomości Unity.
    - `UNT0007`: Unity zastępuje operator porównania null dla unity obiektów, który jest niezgodny z null scalania.
    - `UNT0008`: Unity zastępuje operator porównania null dla unity obiektów, który jest niezgodny z null propagacji.
    - `UNT0009`: Podczas stosowania InitializeOnLoad atrybut do klasy, należy podać konstruktora statycznego. Atrybut InitializeOnLoad zapewnia, że zostanie on wywołany podczas uruchamiania edytora.
    - `UNT0010`: MonoBehaviours powinny być tworzone tylko przy użyciu AddComponent(). MonoBehaviour to składnik, który musi zostać dołączony do obiektu GameObject.
    - `UNT0011`: ScriptableObject powinien być tworzony tylko przy użyciu CreateInstance(). Obiekt ScriptableObject musi zostać utworzony przez aparat Unity do obsługi metod komunikatów aparatu Unity.
    - `USP0001`for: `IDE0029`Unity obiekty nie należy używać null scalania.
    - `USP0002`for: `IDE0031`Unity obiekty nie należy używać propagacji null.
    - `USP0003`for: `IDE0051`Unity komunikaty są wywoływane przez środowisko uruchomieniowe Unity.
    - `USP0004`for `IDE0044`: Pola z atrybutem SerializeField nie powinny być odczytywane tylko w sposób odczytywany.

## <a name="4310"></a>4.3.1.0

Wydano 4 września 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Oceny:**

  - Dodano obsługę lepszego wyświetlania typu, `List<object>` czyli `List'1[[System.Object, <corlib...>]]`zamiast .

  - Dodano obsługę dostępu do elementu członkowskiego `p->data->member`wskaźnika, tj.

  - Dodano obsługę niejawnych konwersji w inicjatorach tablicowych, tj. `new byte [] {1,2,3,4}`

## <a name="4300"></a>4.3.0.0

Wydano 13 sierpnia 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Dodano obsługę protokołu MDS 2.51.

- **Integracji:**

  - Ulepszono okno "Dołącz do instancji Unity" z funkcjami sortowania, wyszukiwania i odświeżania. Pid jest teraz wyświetlany nawet dla graczy lokalnych (przez zapytanie gniazd nasłuchujących w systemie, aby pobrać proces posiadania).

  - Dodano obsługę plików asmdef.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono obsługę nieprawidłowo sformułowanych wiadomości podczas komunikowania się z graczami Unity.

- **Oceny:**

  - Poprawiono obsługę obszarów nazw w wyrażeniach.

  - Poprawiono kontrolę z typami IntPtr.
  
  - Naprawiono problemy z przechodzeniem na przechodzenie z wyjątkami.

  - Poprawiono ocenę pseudo identyfikatorów (takich jak $exception).

  - Zapobiegaj awarii podczas dereferencji nieprawidłowych adresów.  

  - Naprawiono błąd z niezaładowanych appdomains.

## <a name="4201"></a>4.2.0.1

Wydano 24 lipca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano nową opcję tworzenia dowolnego typu plików z Eksploratora projektów Unity.
  
  - Usprawnij buforowanie diagnostyczne podczas korzystania z szybkich kompilacji dla projektów Unity.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono błąd, który powodował, że rozszerzenie pliku nie było obsługiwane przez żadnego znanego edytora.

  - Poprawiono obsługę rozszerzeń niestandardowych w Eksploratorze projektów Unity.

  - Naprawiono ustawienia zapisywania poza głównym okszeniem dialogowym.

  - Usunięto starszą zależność microsoft.VisualStudio.MPF.

## <a name="4110"></a>4.1.1.0

Wydano 24 maja 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Zaktualizowano interfejs API monobehaviour do wersji 2019.1.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono ostrzeżenia raportowania i błędy do wyjścia, gdy włączona jest lekka kompilacja.

  - Poprawiono lekkość wykonania.

## <a name="4100"></a>4.1.0.0

Wydano 21 maja 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę nowego interfejsu API partii, aby szybciej przeładować projekty.

  - Wyłączone pełnej kompilacji dla projektów Unity, na rzecz korzystania z błędów IntelliSense i ostrzeżenia. Rzeczywiście Unity tworzy rozwiązanie Visual Studio z projektów biblioteki klas, które reprezentują, co Unity robi wewnętrznie. Mając na uwadze, że wynik kompilacji w programie Visual Studio nigdy nie jest używany lub odbierane przez Unity jako ich potok kompilacji jest zamknięty. Tworzenie w programie Visual Studio jest po prostu zużywa zasoby za darmo. Jeśli potrzebujesz pełnej kompilacji, ponieważ masz narzędzia lub konfigurację, która zależy od niego, można wyłączyć tę optymalizację (Narzędzia/Opcje/Narzędzia dla Unity/Wyłącz pełną kompilację projektów).

  - Automatycznie wyświetla eksploratora projektu Unity (UPE) po załadowaniu projektu Unity. Upe zostanie zadokowany obok Eksploratora rozwiązań.

  - Zaktualizowano mechanizm wyodrębniania nazw projektów za pomocą unity 2019.x.

  - Dodano obsługę pakietów Unity w UPE. Widoczne są tylko pakiety odniesienia (przy użyciu manifest.json w folderze) `Packages` i pakiety lokalne (osadzone w folderze). `Packages`

- **Generowanie projektu:**

  - Zachowaj właściwości zewnętrzne podczas przetwarzania pliku rozwiązania.

- **Oceny:**

  - Dodano obsługę nazw kwalifikowanych aliasem (na razie tylko globalna przestrzeń nazw). Tak więc oceniający wyrażenie jest teraz akceptowanie typów przy użyciu formularza global::namespace.type.

  - Dodano obsługę `pointer[index]` formularza, który jest semantycznie `*(pointer+index)` identyczny z formą wyłuskania wskaźnika.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono problemy z zależnościami w pliku Microsoft.VisualStudio.MPF.

  - Naprawiono dołączanie odtwarzacza platformy uniwersalnej systemu WSP bez ładowania projektu.

  - Poprawiono automatyczne odświeżanie bazy danych zasobów, gdy program Visual Studio nie został jeszcze dołączony.

  - Naprawiono problemy z motywem z etykietami i polem wyboru.

- **Debuger:**

  - Naprawiono przechodzenie za pomocą konstruktorów statycznych.

## <a name="4005"></a>4.0.0.5

Wydano 27 lutego 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono wykrywanie wersji programu Visual Studio za pomocą pakietu instalacyjnego.

  - Usunięto nieużywane zestawy z pakietu instalacyjnego.

## <a name="4004"></a>4.0.0.4

Wydano 13 lutego 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę prawidłowego wykrywania procesów Unity podczas instalacji i umożliwienia silnikowi konfiguracji lepszego obchodzenia się z blokadami plików.

  - Zaktualizowano `ScriptableObject` interfejs API.

## <a name="4003"></a>4.0.0.3

Wydano 31 stycznia 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Pola publiczne i serializowane nie będą już powodować ostrzeżeń. Mamy automatycznie pomijane `CS0649` ostrzeżenia `IDE0051` i kompilatora w projektach Unity, które utworzyły te komunikaty.

- **Integracji:**

  - Poprawiono środowisko użytkownika do wyświetlania edytora Unity i wystąpień odtwarzacza (okna są teraz o zmiennym rozmiarze, użyj jednolitych marginesów i wyświetlają uchwyt zmiany rozmiaru). Dodano informacje o identyfikatorze procesu dla edytorów Unity.

  - Zaktualizowano `MonoBehaviour` interfejs API.

- **Oceny:**

  - Dodano obsługę funkcji lokalnych.

  - Dodano obsługę pseudo zmiennych (identyfikatory wyjątków i obiektów).

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono błąd, który powodował, że obrazy i motywy monikerów.

  - Zapisuj tylko w oknie wyjściowym podczas debugowania, gdy automatycznie odświeża bazę danych zasobów.

  - Naprawiono opóźnienia interfejsu użytkownika podczas filtrowania kreatora MonoBehaviour.

- **Debuger:**

  - Poprawiono odczytywanie atrybutu niestandardowego na nazwanych argumentów podczas korzystania ze starych wersji protokołu.

## <a name="4002"></a>4.0.0.2

Wydano 23 stycznia 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Poprawiono eksperymentalne generowanie kompilacji.

  - Poprawiono obsługę zdarzeń pliku projektu, aby zminimalizować ciśnienie wątku interfejsu użytkownika.

  - Naprawiono dostawcę uzupełniania z zmianami tekstu wsadowego.

- **Debuger:**

  - Naprawiono wyświetlanie komunikatów debugowania użytkownika do dołączonego debugera.

## <a name="4001"></a>4.0.0.1

Wydano 10 grudnia 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Oceny:**

  - Zastąpiono NRefactory na rzecz Roslyn do oceny wyrażenia.

  - Dodano obsługę wskaźników: wyłuskanie, rzutowanie i arytmetyka wskaźnika (w tym celu wymagane są zarówno Unity 2018.2+, jak i nowe środowisko wykonawcze).

  - Dodano obsługę widoku wskaźnika tablicy (jak w języku C++). Weź wyrażenie wskaźnika, a następnie dołącz przecinek i liczbę elementów, które chcesz zobaczyć.

  - Dodano obsługę konstrukcji asynchronii.

- **Integracji:**

  - Dodano obsługę automatycznego odświeżania bazy danych zasobów Unity przy zapisywaniu. Jest to domyślnie włączone i wyzwoli ponowną kompilację po stronie Unity podczas zapisywania skryptu w programie Visual Studio. Tę funkcję można wyłączyć w obszarze Narzędzia\Opcje\Narzędzia dla unity\Refresh Unity's AssetDatabase przy zapisywaniu.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono aktywację mostka, gdy program Visual Studio nie jest wybrany jako preferowany edytor zewnętrzny.

  - Poprawiono ocenę wyrażenia z nieprawidłowo sformułowanych lub nieobsługiwałych wyrażeń.

## <a name="4000"></a>4.0.0.0

Wydano 4 grudnia 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę programu Visual Studio 2019 (potrzebujesz co najmniej Unity 2018.3, aby móc używać programu Visual Studio 2019 jako zewnętrznego edytora skryptów).

  - Przyjęto usługę obrazu i katalog programu Visual Studio z pełną obsługą skalowania HDPI, doskonałych obrazów pikseli i motywów.

### <a name="deprecated-features"></a>Przestarzałe funkcje

- **Integracji:**

  - W przyszłości narzędzia programu Visual Studio dla unity będą obsługiwać tylko unity 5.2+ (z wbudowaną integracją programu Unity w programie Visual Studio).

  - W przyszłości narzędzia programu Visual Studio dla unity będą obsługiwać tylko program Visual Studio 2015+.

  - Usunięto starszą usługę językową, listę błędów i pasek stanu.

  - Usunięto Kreatora szybkiego monobehaviouru (na rzecz dedykowanej obsługi intellisense).

## <a name="3903"></a>3.9.0.3

Wydano 28 listopada 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono problemy z przeładowaniem projektu i intellisense podczas dodawania lub usuwania skryptów znajdujących się w pierwszym projekcie.

## <a name="3902"></a>3.9.0.2

Wydana 19 listopada 2018 r.Released November 19, 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono zakleszczenie w bibliotece używane do komunikowania się z aparatem debugera Unity, co spowodowało zamrożenie programu Visual Studio lub Unity, szczególnie podczas uderzania "Dołącz do jedności" lub ponownego uruchamiania gry.

## <a name="3901"></a>3.9.0.1

Wydano 15 listopada 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono aktywację wtyczki Unity, gdy wybrano inny domyślny edytor.

## <a name="3900"></a>3.9.0.0

Wydano 13 listopada 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Wycofane obejście problemu wydajności Unity, który został naprawiony przez Unity.

## <a name="3807"></a>3.8.0.7

Wydano 20 września 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - (Backported od 3.9.0.2) Naprawiono zakleszczenie w bibliotece używane do komunikowania się z aparatem debugera Unity, co spowodowało zamrożenie programu Visual Studio lub Unity, szczególnie podczas uderzania "Dołącz do jedności" lub ponownego uruchamiania gry.

## <a name="3806"></a>3.8.0.6

Wydana 27 sierpnia 2018 r.Released August 27, 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono przeładowanie projektów i rozwiązań.

## <a name="3805"></a>3.8.0.5

Wydana 20 sierpnia 2018 r.Released August 20, 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Poprawiono utylizację subskrypcji monitorowania projektu.

## <a name="3804"></a>3.8.0.4

Wydano 14 sierpnia 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Oceny:**

  - Dodano obsługę wartości wskaźnika.

  - Dodano obsługę metod ogólnych.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Inteligentne przeładowanie z wieloma projektami zmienionymi.

## <a name="3803"></a>3.8.0.3

Wydana 24 lipca 2018 r.Released July 24, 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - (Backported od 3.9.0.0) Wycofane obejście problemu wydajności Unity, który został naprawiony przez Unity.

## <a name="3802"></a>3.8.0.2

Wydano 7 lipca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Obejście przejściowe dla błędu wydajności Unity: pamięć podręczna MonoIslands podczas generowania projektów.

## <a name="3801"></a>3.8.0.1

Wydana 26 czerwca 2018 r.Released June 26, 2018

### <a name="new-features"></a>Nowe funkcje

- **Debugowania:**

  - Dodano obsługę poleceń UserLog i UserBreak.

  - Dodano obsługę z opóźnieniem obciążenia typu (optymalizacja opóźnienia ładowania sieci i debugera odpowiedzi).

### <a name="bug-fixes"></a>Poprawki błędów

- **Oceny:**

  - Ulepszona ocena ekspresji operatora binarnego i wyszukiwanie metod.

## <a name="3800"></a>3.8.0.0

Wydana 30 maja 2018 r.Released May 30, 2018

### <a name="new-features"></a>Nowe funkcje

- **Debugowania:**

  - Dodano obsługę wyświetlania zmiennych w konstrukcjach asynchronizowych.

  - Dodano obsługę przetwarzania typów zagnieżdżonych podczas ustawiania punktów przerwania, aby zapobiec ostrzeżeniom z konstrukcjami kompilatora.

- **Integracji:**

  - Dodano obsługę gramatyki tekstu dla modułów cieniowania (obciążenie języka C++ nie jest już potrzebne do kolorowania kodu modułu cieniującego).

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Nie należy już konwertować przenośnej pdb do mdb podczas korzystania z nowego środowiska wykonawczego Unity.

## <a name="3701"></a>3.7.0.1

Wydana 7 maja 2018 r.Released May 7, 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Instalator:**

  - Naprawiono problem zależności podczas korzystania z kompilacji eksperymentalnych.

## <a name="3700"></a>3.7.0.0

Wydana 7 maja 2018 r.Released May 7, 2018

### <a name="new-features"></a>Nowe funkcje

- **Debugowania:**

  - Dodano obsługę zaaranżowanego debugowania (debugowanie wielu graczy/edytora z tą samą sesją programu Visual Studio).

  - Dodano obsługę debugowania odtwarzacza USB systemu Android.

  - Dodano obsługę debugowania odtwarzaczy UWP/IL2CPP.

- **Oceny:**

  - Dodano obsługę specyfikatorów szesnastkowych.

  - Ulepszone doświadczenie oceny okna zegarka.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Poprawiono użycie ustawień wyjątków.

- **Generowanie projektu:**

  - Wyklucz jednostki kompilacji menedżera pakietów z generacji.

## <a name="3605"></a>3.6.0.5

Wydana 13 marca 2018 r.Released March 13, 2018

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano wsparcie dla nowego generatora projektów w Unity 2018.1.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono obsługę uszkodzonych stanów za pomocą projektów niestandardowych.

- **Debuger:**

  - Poprawiono ustawienie następnej instrukcji.

## <a name="3604"></a>3.6.0.4

Wydano 5 marca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono wykrywanie wersji mono.

- **Integracji:**

  - Naprawiono problemy z pomiarem czasu z 2018.1 i aktywacją wtyczki.

## <a name="3603"></a>3.6.0.3

Wydana 23 lutego 2018 r.Released February 23, 2018

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę standardu .NET.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono wykrywanie struktury docelowej unity.

- **Debuger:**

  - Naprawiono łamanie wyjątków, które są generowane poza usercode.

## <a name="3602"></a>3.6.0.2

Wydano 7 lutego 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Zaktualizuj powierzchnię interfejsu API UnityMessage dla 2017.3.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Przeładuj tylko projekty na zmiany zewnętrzne (z ograniczaniem przepustowości).

## <a name="3601"></a>3.6.0.1

Wydano 24 stycznia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono automatyczną konwersję symboli debugowania pdb do mdb.

  - Naprawiono pośrednie wywołanie EditorPrefs.GetBool wpływ inspektora podczas próby zmiany rozmiaru tablicy.

## <a name="3600"></a>3.6.0.0

Wydano 10 stycznia 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę modelu referencyjnego MonoIsland 2018.1.

- **Oceny:**

  - Dodano obsługę identyfikatora $exception.

- **Debuger:**

  - Dodano obsługę atrybutów DebuggerHidden/DebuggerStepThrough z nowym czasem wykonywania Unity.

- **Kreatorów:**

  - Wprowadzenie "Najnowszej" wersji dla kreatorów.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Poprawiono obliczanie identyfikatora guid projektu dla projektów graczy.

- **Debuger:**

  - Naprawiono wyścig w obsłudze zdarzeń łamania.

- **Kreatorów:**

  - Odśwież kontekst roslyn przed wstawieniem metody.

## <a name="3503"></a>3.5.0.3

Wydano 9 stycznia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono automatyczną konwersję symboli debugowania pdb do mdb.

## <a name="3502"></a>3.5.0.2

Wydano 4 grudnia 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Projekty Unity są teraz automatycznie ponownie ładowane w programie Visual Studio po dodaniu skryptu do środowiska Unity lub jego usunięciu.

- **Debuger:**

  - Dodano opcję używania debugera mono udostępnionego przez platformę Xamarin i visual studio dla komputerów Mac do debugowania Edytora Unity.

  - Dodano obsługę przenośnych plików symboli debugowania.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązane problemy z zależnościami dotyczącymi konfiguracji.

  - Poprawiono menu pomocy interfejsu API Unity nie jest wyświetlane.

- **Generowanie projektu:**

  - Naprawiono generowanie projektów graczy podczas pracy nad grą uwp z zapleczem IL2CPP/.NET 4.6.

  - Naprawiono dodatkowe rozszerzenie dll niesłusznie dodane do nazwy pliku złożenia.

  - Poprawiono użycie określonego poziomu zgodności interfejsu API projektu zamiast globalnego.

  - Nie wymuszaj AllowAttachedDebuggingOfEditor Unity flagi jako domyślne jest teraz "true".

## <a name="3402"></a>3.4.0.2

Wydana 19 września 2017 r.Released September 19, 2017

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę jednostek kompilacji assembly.json.

  - Zatrzymano kopiowanie zestawów Unity do folderu projektu.

- **Debuger:**

  - Dodano obsługę ustawiania następnej instrukcji z nowym środowiskiem uruchomienim Unity.

  - Dodano obsługę typu dziesiętnego z nowym czasem wykonywania Unity.

  - Dodano obsługę konwersji niejawnych/jawnych.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oceny:**

  - Poprawiono tworzenie tablicy o niejawne rozmiary.

  - Naprawiono elementy generowane przez kompilator z miejscowymi.

- **Generowanie projektu:**

  - Poprawiono odwołanie do microsoft.cSharp dla poziomu interfejsu API 4.6.

## <a name="3302"></a>3.3.0.2

Wydana 15 sierpnia 2017 r.Released August 15, 2017

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono generowanie rozwiązania programu Visual Studio w unity 5.5 i poprzednich wersjach.

## <a name="3300"></a>3.3.0.0

Wydana 14 sierpnia 2017 r.Released August 14, 2017

### <a name="new-features"></a>Nowe funkcje

- **Oceny:**

  - Dodano obsługę tworzenia struktur z nowym środowiskom run unity.

  - Dodano minimalistyczną obsługę wskaźników.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oceny:**

  - Naprawiono wywołanie metody na prymitywach.

  - Poprawiono ocenę pola z typami oznaczonymi symbolem BeforeFieldInit.

  - Naprawiono nieobjęte połączenia z operatorami binarnymi (substract).

  - Naprawiono problemy podczas dodawania elementów do programu Visual Studio Watch.

- **Generowanie projektu:**

  - Poprawiono odwołania do nazw zestawu za pomocą plików mcs.rsp.

  - Poprawiono definicje z poziomami INTERFEJSU API.

## <a name="3200"></a>3.2.0.0

Wydana 10 maja 2017 r.Released May 10, 2017

### <a name="new-features"></a>Nowe funkcje

- **Instalator:**

  - Dodano obsługę czyszczenia pamięci podręcznej MEF.

### <a name="bug-fixes"></a>Poprawki błędów

- **Edytor kodu:**

  - Poprawiono klasyfikację/uzupełnianie z atrybutami niestandardowymi.

  - Naprawiono migotanie za pomocą komunikatów Unity.

## <a name="3100"></a>3.1.0.0

Wydana 7 kwietnia 2017 r.Released April 7, 2017

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Dodano obsługę nowego środowiska wykonawczego Unity (ze zgodnością .NET 4.6 / C# 6).

- **Generowanie projektu:**

  - Dodano obsługę profilu .NET 4.6.

  - Dodano obsługę plików mcs.rsp.

  - Zawsze włączaj niebezpieczny przełącznik kompilacji, gdy używana jest unity 5.6.

  - Dodano obsługę generowania projektów "Player" podczas korzystania z platformy Sklepu Windows i zaplecza il2cpp.

### <a name="bug-fixes"></a>Poprawki błędów

- **Edytor kodu:**

  - Poprawiono pozycję szycie po wstawieniu metody z automatycznym uzupełnianiem.

- **Generowanie projektu:**

  - Usunięto wersję zestawu do postprocesji.

## <a name="3001"></a>3.0.0.1

Wydano 7 marca 2017 r.

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Ta wersja zawiera wszystkie nowe funkcje i poprawki błędów wprowadzone z serii 2.8.x.

## <a name="2820---30-preview-3"></a>2.8.2.0 - 3.0 Podgląd 3
Wydano 25 stycznia 2017 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono regresję, w której wtyczki były projektowane dwukrotnie, najpierw jako binarna biblioteka DLL, a następnie jako odwołanie do projektu.

## <a name="2810---30-preview-2"></a>2.8.1.0 - 3.0 Podgląd 2
Wydano 23 stycznia 2017 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Edytor kodu:**

  - Naprawiono awarię podczas uruchamiania deklaracji atrybutu bez uzupełniania stężenia.

- **Debuger:**

  - Poprawiono punkty przerwania funkcji z coroutines w nowym kompilatorze/czasie wykonywania Unity.

  - Dodano ostrzeżenie w przypadku niezwiązanego punktu przerwania (gdy nie zostanie znaleziona odpowiednia lokalizacja źródła).

- **Generowanie projektu:**

  - Naprawiono generowanie csprojów ze specjalnymi/zlokalizowanych znaków.

  - Poprawiono odwołania poza zasobami, takimi jak Biblioteka (np. sdk Facebooka).

- **Pozostałe:**

  - Dodano czek, aby zapobiec uruchamianiu unity podczas instalacji lub odinstalowywania.

  - Przełączony na https do zdalnej dokumentacji Unity.

## <a name="2800---30-preview"></a>2.8.0.0 - 3.0 Podgląd
Wydana 17 listopada 2016 r.Released November 17, 2016

### <a name="new-features"></a>Nowe funkcje

- **Ogólne:**

  - Dodano obsługę instalatora programu Visual Studio 2017.

  - Dodano obsługę rozszerzeń programu Visual Studio 2017.

  - Dodano obsługę lokalizacji.

- **Edytor kodu:**

  - Dodano c# IntelliSense dla komunikatów Unity.

  - Dodano kolorowanie kodu C# dla komunikatów Unity.

- **Debuger:**

  - Dodano obsługę `is` `as`wyrażeń `default`, `new` , rzutów bezpośrednich, ,.

  - Dodano obsługę wyrażeń concat ciąg.

  - Dodano obsługę szesnastkowego wyświetlania wartości całkowitych.

  - Dodano obsługę tworzenia nowych zmiennych tymczasowych (instrukcji).

  - Dodano obsługę niejawnych konwersji pierwotnych.

  - Dodano lepsze komunikaty o błędach, gdy typ jest oczekiwany lub nie znaleziono.

- **Generowanie projektu:**

  - Usunięto sufiks CSharp z nazw projektu.

  - Usunięto odwołanie do pliku docelowego msbuild o szerokim systemie.

- **Kreatorów:**

  - Dodano obsługę komunikatów Unity w typach innych niż zachowanie, takich jak Edytor lub EditorWindow.

  - Przełączony na Roslyn, aby wstrzyknąć i sformatować komunikaty Unity.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono błąd awarii Unity podczas oceny typów ogólnych.

  - Poprawiono obsługę typów nullable.

  - Poprawiono obsługę wyliczenia.

  - Poprawiono obsługę zagnieżdżonych typów elementów członkowskich.

  - Poprawiono dostęp do indeksatora kolekcji.

  - Poprawiono obsługę ramek iteratora debugowania za pomocą nowego kompilatora języka C#.

- **Generowanie projektu:**

  - Naprawiono błąd, który uniemożliwiał kompilację podczas kierowania na odtwarzacz sieci Web Unity.

  - Naprawiono błąd, który uniemożliwiał kompilację podczas kompilowania skryptu o nazwie pliku zakodowanego w sieci Web.

## <a name="2300"></a>2.3.0.0

Wydana 14 lipca 2016 r.Released July 14, 2016

### <a name="new-features"></a>Nowe funkcje

- **Ogólne:**

  - Dodano opcję wyłączania dzienników konsoli Unity na liście błędów programu Visual Studio.

  - Dodano opcję umożliwiającą modyfikowanie wygenerowanych właściwości projektu.

- **Debuger:**

  - Dodano wizualizatory ciągów tekstowych, XML, HTML i JSON.

- **Kreatorów:**

  - Dodano brakujące zachowania MonoBehaviors.

### <a name="bug-fixes"></a>Poprawki błędów

- **Ogólne:**

  - Naprawiono konflikt z ReSharper, który uniemożliwiał formanty wewnątrz ustawienia programu Visual Studio.

  - Naprawiono konflikt z xamarin, który uniemożliwił debugowanie w niektórych przypadkach.

- **Debuger:**

  - Naprawiono błąd, który powodował zawieszanie się programu Visual Studio podczas debugowania.

  - Naprawiono błąd z punktami przerwania funkcji w programie Visual Studio 2015.

  - Naprawiono kilka problemów z oceną wyrażenia.

## <a name="2200"></a>2.2.0.0

Wydana 4 lutego 2016 r.Released February 4, 2016

### <a name="new-features"></a>Nowe funkcje

- **Kreatorów:**

  - Dodano inteligentne wyszukiwanie w kreatorze **Implementuj monobehavior.**

  - Uświadomił kontekst kreatorów; na przykład NetworkBehavior wiadomości są dostępne tylko podczas pracy z NetworkBehavior.

  - Dodano obsługę komunikatów NetworkBehavior w kreatorach.

- **Interfejsu użytkownika:**

  - Dodano opcję konfigurowania widoczności komunikatów MonoBehavior.

  - Usunięto strony właściwości programu Visual Studio, które nie są istotne dla projektów Unity.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Poprawiono odniesienia do UnityEngine i UnityEditor na Unity 4.6.

  - Poprawiono generowanie plików projektu, gdy Unity jest uruchomiona na OSX.

  - Poprawiono obsługę nazw projektów zawierających znaki skrótu (#).

  - Ograniczone wygenerowane projekty do języka C# 4.

- **Debuger:**

  - Naprawiono błąd z oceną wyrażenia podczas debugowania wewnątrz coroutine Unity.

  - Naprawiono błąd, który powodował zawieszanie się programu Visual Studio podczas debugowania.

- **Interfejsu użytkownika:**

  - Naprawiono niezgodność z rozszerzeniem [Tabs Studio](https://tabsstudio.com/) Visual Studio.

- **Instalator:**

  - Obsługa instalacji vstu na całym komputerze (instalacja dla wszystkich użytkowników) przez tworzenie wpisów rejestru HKLM.

  - Rozwiązaliśmy problemy z dezinstalacją vstu, gdy ta sama wersja vstu jest zainstalowany dla wielu różnych wersji programu Visual Studio. Na przykład po zainstalowaniu vstu **2015** 2.1.0.0 i VSTU **2013** 2.1.0.0.

## <a name="2100"></a>2.1.0.0

Wydana 8 września 2015 r.Released September 8, 2015

### <a name="new-features"></a>Nowe funkcje

- Wsparcie dla jedności 5.2

### <a name="bug-fixes"></a>Poprawki błędów

- Wyświetlanie pozycji menu na Unity < 4.2

- Komunikat o błędzie nie jest już wyświetlany, gdy program Visual Studio blokuje pliki intellisense XML.

- Obsługa <\<po zmianie>> warunkowe punkty przerwania, gdy argument warunkowy nie jest wartością logiczną.

- Poprawiono odwołania do zestawów UnityEngine i UnityEditor dla aplikacji ze Sklepu Windows.

- Naprawiono błąd podczas przechodzenia do debugera: Nie można przejść, wyjątek ogólny.

- Poprawiono punkty przerwania liczby trafień w programie Visual Studio 2015.

## <a name="2000"></a>2.0.0.0

Wydana 20 lipca 2015 r.Released July 20, 2015

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja jedności:**

  - Naprawiono konwersję symboli debugowania utworzonych za pomocą programu Visual Studio 2015 podczas importowania biblioteki DLL i jej symboli debugowania (PDB).

  - Zawsze generuj pliki MDB podczas importowania biblioteki DLL i jej symboli debugowania (PDB), z wyjątkiem sytuacji, gdy dostępny jest również plik MDB.

  - Naprawiono zanieczyszczenie katalogu projektu Unity za pomocą katalogu obj.

  - Poprawiono generowanie odwołań do systemów.Xml.Link i System.Runtime.Serialization.

  - Dodano obsługę wielu subskrybentów do haków interfejsu API generowania plików projektu.

  - Zawsze należy ukończyć generowanie pliku projektu, nawet jeśli jeden z plików, które mają zostać wygenerowane, jest zablokowany.

  - Dodano obsługę * symboli wieloznacznych w filtrze rozszerzenia podczas określania plików, które mają być uwzględnione w projekcie C#.

- **Integracja z programem Visual Studio:**

  - Naprawiono błąd ze zgodnością z narzędziami zasilania produktywności.

  - Poprawiono generowanie MonoBehaviors wokół zdarzeń i delegatów deklaracji.

- **Debuger:**

  - Naprawiono potencjalne zamrożenie podczas debugowania.

  - Naprawiono błąd, który powodował, że miejscowi nie byli wyświetlani w niektórych klatkach stosu.

  - Poprawiono sprawdzanie pustych tablic.

## <a name="1990---20-preview-2"></a>1.9.9.0 - 2.0 Podgląd 2
Wydana 2 kwietnia 2015 r.Released April 2, 2015

### <a name="new-features"></a>Nowe funkcje

- **Eksplorator projektu Unity:**

  - Automatyczna zmiana nazwy klasy podczas zmiany nazwy pliku w Eksploratorze projektu Unity (zobacz okno dialogowe **Opcje).**

  - Automatycznie wybierz nowo utworzone skrypty w Eksploratorze projektów Unity.

  - Śledzenie aktywnego skryptu w Eksploratorze projektu Unity (zobacz **opcje** w oknie dialogowym).

  - Podwójna synchronizacja Eksploratora rozwiązań programu Visual Studio (zobacz okno dialogowe **Opcje).**

  - Zaadoptuj ikony programu Visual Studio w Eksploratorze projektu Unity.

- **Debuger:**

  - Wybierz aktywny cel debugowania z listy zapisanych lub ostatnio używanych obiektów docelowych debugowania (zobacz okno dialogowe **Opcje).**

  - Tworzenie punktów przerwania funkcji na Metody MonoBehavior i zastosować je do wielu klas MonoBehavior.

  - Obsługa make identyfikator obiektu w debugerze.

  - Obsługa liczby trafień punktu przerwania w debugerze.

  - Obsługa break-on-exception w debugerze (Experimental. Zobacz Okno dialogowe **opcji).**

  - Obsługa tworzenia obiektów i tablic podczas oceny wyrażeń w debugerze.

  - Obsługa porównania null, gdy wyrażenia oceny w debugerze.

  - Odfiltruj przestarzałych członków w oknach zegarka debugera.

- **Instalator:**

  - Zoptymalizowane narzędzia programu Visual Studio dla rejestracji rozszerzenia Unity.

  - Zainstaluj pakiet Visual Studio Tools for Unity dla unity 5.

- **Dokumentacja:** Zwiększ wydajność generowania dokumentacji.

- **Kreatorzy:** Obsługa nowych metod MonoBehavior dla Unity 4.6 i Unity 5.

- **Jedność:** Wyszukiwanie niebezpiecznych flag i niestandardowych zdefiniowanych w plikach rsp podczas generowania pliku projektu.

- **Interfejs użytkownika:** Dodano okno dialogowe Narzędzia programu Visual Studio dla **opcji** unity w programie Visual Studio.

### <a name="bug-fixes"></a>Poprawki błędów

- **Eksplorator projektu Unity:**

  - Odśwież Eksploratora projektu Unity po przeniesieniu lub zmianie nazwy plików z Eksploratora rozwiązań programu Visual Studio.

  - Zachowaj zaznaczenia podczas zmiany nazwy plików w Eksploratorze projektów Unity.

  - Zapobiegaj automatycznemu rozwijaniu i zwijaniu, gdy pliki są dwukrotnie klikane w Eksploratorze projektów Unity.

  - Upewnij się, że nowo wybrane pliki są widoczne w Eksploratorze projektów Unity.

- **Debuger:**

  - Zapobiec możliwemu zamrożeniu programu Visual Studio podczas oceny wyrażeń w debugerze.

  - Upewnij się, że wywołania metody w odpowiedniej domenie w debugerze.

- **Jedność:**

  - Popraw lokalizację UnityVS.OpenFile z Unity 5.

  - Popraw lokalizację pdb2mdb z Unity 5.

  - Zapobiegaj możliwemu wyjątkowi podczas generowania plików projektu.

  - Zapobiec możliwemu zamrożeniu podczas uruchamiania Unity na OSX.

  - Obsługa wyjątków wewnętrznych.

  - Wyślij dzienniki konsoli Unity do listy błędów vs.

- **Dokumentacja:** Poprawne generowanie dokumentacji dla nowej dokumentacji jedności.

- **Projekt:** Przenieś i zmień nazwę plików .meta Unity w razie potrzeby, nawet w folderach.

- **Kreatorzy:** Popraw kolejność parametrów metody MonoBehavior podczas generowania kodu.

- **Interfejs użytkownika:** Obsługa motywów programu Visual Studio dla menu kontekstowego i ikon.

## <a name="1980---20-preview"></a>1.9.8.0 - 2.0 Podgląd
Wydana 12 listopada 2014 r.Released November 12, 2014

### <a name="new-features"></a>Nowe funkcje

- Obsługa programu Visual Studio 2015.

- Kolorowanie kodu dla modułów cieniowania Unity w programie Visual Studio 2015.

- Ulepszona wizualizacja wartości podczas debugowania:

  - Lepsza wizualizacja list tablic, list, hashtables i słowników.

  - Pokaż niepublicznych członków i statycznych członków jako kategorie w zegarku i widokach lokalnych.

  - Ulepszone wyświetlanie właściwości SerializedProperty unity, aby ocenić tylko pole wartości prawidłowe dla właściwości.

  - DebuggerDisplayAttribute wsparcie dla klas i struktur.

  - DebuggerTypeProxyAttribute wsparcie.

- Należy dokonać wstawiania metod MonoBehaviour przy użyciu naszych kreatorów do przestrzegania konwencji kodowania użytkownika.

- Implementowanie obsługi szablonów tekstu czas kompilacji w unityvs projektów generowanych.

- Implementuj obsługę zasobów ResX w projektach generowanych przez UnityVS.

- Obsługa programów cieniowania otwierania w programie Visual Studio z unity.

### <a name="bug-fixes"></a>Poprawki błędów

- Oczyść gniazda przed rozpoczęciem gry w Unity po dołączeniu i odtworzeniu został wyzwolony w programie Visual Studio. Rozwiązuje to niektóre problemy ze stabilnością połączenia między Unity i VS podczas korzystania z Dołączania i Odtwarzania.

- Unikaj wywoływania metod w interfejsie debugera aparatu skryptów Unity, które są podatne na zamrożenie Unity. Spowoduje to naprawienie zamrożenia unity podczas dołączania debugera.

- Napraw wyświetlanie połączeń, gdy nie są dostępne żadne symbole.

- Nie rejestruj wywołania zwrotnego dziennika, jeśli nie musimy.

## <a name="1920"></a>1.9.2.0

Wydana 9 października 2014 r.Released October 9, 2014

### <a name="new-features"></a>Nowe funkcje

- Usprawnij wykrywanie graczy Unity.

- Korzystając z naszego otwieracza plików, upewnij się, że Unity przekazuje numer wiersza, a także nazwę pliku.

- Domyślnie w dokumentacji unity online, jeśli nie ma dokumentacji lokalnej.

### <a name="bug-fixes"></a>Poprawki błędów

- Napraw potencjalną awarię Unity po uderzeniu w punkt przerwania po ponownym załadowaniu domeny.

- Napraw wyjątki wyświetlane w konsoli Unity podczas zamykania naszych okien konfiguracji lub informacje, po ponownym załadowaniu domeny.

- Napraw wykrywanie 64bits Unity działa lokalnie.

- Napraw filtrowanie monobepogody na wersję Unity w kreatorach.

- Napraw błąd, w którym wszystkie zasoby zostały uwzględnione w plikach projektu, jeśli filtr rozszerzenia był pusty.

## <a name="1910"></a>1.9.1.0

Wydana 22 września 2014 r.Released September 22, 2014

### <a name="new-features"></a>Nowe funkcje

- Optymalizuj punkt przerwania wiązania do lokalizacji źródłowych.

- Obsługa przeciążonych metod w ocenie wyrażeń debugera.

- Obsługa elementów pierwotnych boksu i typów wartości w ocenie wyrażeń debugera.

- Obsługa ponownego tworzenia środowiska zmiennych lokalnych języka C# podczas debugowania metod anonimowych.

- Usuń i zmień nazwę plików .meta podczas usuwania lub zmieniania nazwy plików z programu Visual Studio.

### <a name="bug-fixes"></a>Poprawki błędów

- Napraw obsługę motywów programu Visual Studio. Wcześniej okna dialogowe na czarnych motywach mogły być puste.

- Napraw jedność zamrożenie podczas łączenia debugera, gdy Unity jest ponowne kompiowanie.

- Napraw punkty przerwania podczas debugowania zdalnych edytorów lub odtwarzaczy skompilowanych w innym systemie.

- Napraw ewentualną awarię programu Visual Studio po osiągnięciu punktu przerwania.

- Napraw powiązania punktów przerwania, aby uniknąć punktów przerwania pokazano jako nieładne.

- Napraw obsługę zakresu zmiennych w debugerze, aby uniknąć zmiennych na żywo, które pojawiają się poza zakresem.

- Napraw wyszukiwanie statycznych elementów członkowskich w ocenie wyrażeń debugera.

- Napraw wyświetlanie typów w ocenie wyrażeń debugera, aby wyświetlić pola statyczne i właściwości.

- Napraw generowanie rozwiązania, gdy nazwy projektu Unity zawiera znaki specjalne, które visual studio zabrania (Połącz problem #948666).

- Napraw pakiet Unity narzędzi programu Visual Studio Tools, aby natychmiast zatrzymać wysyłanie zdarzeń konsoli po odznaczeniu opcji (problem z połączeniem #933357).

- Napraw wykrywanie odwołań, aby poprawnie ponownie wygenerować odwołania do nowych interfejsów API, takich jak UnityEngine.UI w projektach generowanych przez UnityVS.

- Napraw instalatora, aby wymagać, aby program Visual Studio został zamknięty przed instalacją, aby uniknąć uszkodzonych instalacji.

- Napraw instalatora, aby zainstalować zestawy odwołań Unity jako odpowiedni składnik autonomiczny, współużytkowany przez wszystkie wersje vstu.

- Napraw skrypty otwierające za pomocą vstu w 64-bitowych wersjach Unity.

## <a name="1900"></a>1.9.0.0

Wydana 29 lipca 2014 r.Released July 29, 2014

### <a name="new-features"></a>Nowe funkcje

- W oknie Dołączanie debugera unity dodaj możliwość wprowadzania niestandardowego adresu IP i portu do debugowania.

- Dodaj opcję konfiguracji, aby ustawić Unity do pracy w tle, czy nie.

- Dodaj opcję konfiguracji, aby wygenerować tylko pliki rozwiązania i projektu lub pliki projektu.

- Cel uruchamiania: wybierz dołącz do unity lub Dołącz do jedności i odtwórz.

- Wyświetlanie tablic wielowymiarowych w debugerze.

- Obsługa nowych portów debugowania odtwarzacza Unity.

- Obsługa odwołań do nowych zestawów Unity, takich jak zestawy 4.6 GUI unity.

- Dekonstruuje zamknięcia, aby prawidłowo wyświetlać zmienne lokalne podczas debugowania.

- Dekonstrukcje generowane zmienne iteratorów do argumentów podczas debugowania.

- Zachowaj stan Eksploratora projektu Unity po ponownym załadowaniu projektu.

- Dodaj polecenie, aby zsynchronizować Eksploratora projektu Unity z bieżącym dokumentem.

### <a name="bug-fixes"></a>Poprawki błędów

- Napraw warunkowe punkty przerwania, których warunki są ustawione przed uruchomieniem debugera.

- Napraw odwołania do UnityEngine, aby uniknąć ostrzeżeń.

- Napraw wersje analizy dla wersji beta Unity.

- Rozwiązać problem, w którym zmienne nie będą wyświetlane w oknie zmiennych lokalnych podczas uderzania w punkt przerwania lub stepping.

- Napraw etykietki narzędzi zmiennych w programie Visual Studio 2013.

- Napraw generowanie dokumentacji IntelliSense dla Unity 4.5.

- Napraw komunikację Unity / Visual Studio po przeładowaniu domeny (play/stop w Unity).

- Napraw obsługę części motywów programu Visual Studio.

> [!IMPORTANT]
> C# jest dominującym językiem w ekosystemie Unity — nowe przykładowe zasoby znajdują się w języku C#, dokumentacja Unity będzie domyślnie C# — usunęliśmy nasze podstawowe wsparcie dla UnityScript i Boo, aby lepiej skupić się na doświadczeniu języka C#. W rezultacie rozwiązania VSTU są teraz tylko w języku C# i są znacznie szybsze do załadowania.

## <a name="1820"></a>1.8.2.0

Wydano 7 stycznia 2014 r.

### <a name="new-features"></a>Nowe funkcje

- Obejść problem w warstwie sieciowej aparatu skryptów Unity na Mavericks do zdalnego odnajdywania edytorów.

- Obsługa nowych portów w celu wykrywania zdalnych odtwarzaczy Unity.

- Odwołanie UnityEngine zestaw specyficzne dla bieżącego obiektu docelowego kompilacji.

- Dodaj ustawienie do filtrowania plików do uwzględnienia w wygenerowanych projektach.

- Dodaj ustawienie, aby wyłączyć wysyłanie dzienników konsoli do listy błędów programu Visual Studio. Jest to przydatne, jeśli używasz PlayMaker lub Console Pro, ponieważ w Unity może być zarejestrowane tylko jedno wywołanie zwrotne w celu odbierania dzienników konsoli.

- Dodaj ustawienie, aby wyłączyć generowanie symboli debugowania mdb. Jest to przydatne, jeśli generujesz mdb samodzielnie.

### <a name="bug-fixes"></a>Poprawki błędów

- Napraw regresję, gdy pliki otwarte w programie VS z Unity >= 4.2 utraciłoby IntelliSense.

- Napraw nasze okna dialogowe vs do obsługi motywów niestandardowych.

- Napraw zamknięcie menu kontekstowego UPE.

- Zapobiegaj awarii w Unity, gdy wersja określonego wygenerowanego zestawu, jeśli nie jest zsynchronizowany.

## <a name="1810"></a>1.8.1.0

Wydana 21 listopada 2013 r.Released November 21, 2013

### <a name="new-features"></a>Nowe funkcje

- Dostosowano kreatorów MonoBehaviour za pomocą interfejsów API Unity 4.3.

- Kreatorzy monobepogody filtrują interfejsy API unity w zależności od używanej wersji.

- Dodaj odwołanie do System.Xml.Linq do projektów dla Unity > 4.1.

- Prettify nasze wywołania debug.log, aby nie zawierać początek stacktrace w wiadomości.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono błąd, który powodował, że zakłócaliśmy domyślną obsługę plików JavaScript w programie Visual Studio.

- Naprawiono biały piksel pojawiający się w VS, dla rzeczywistego tym razem.

- Naprawiono usunięcie UnityVS.VersionSpecific zestawu, jeśli jest oznaczony jako odczyttylko przez SCM.

- Poprawiono wyjątki podczas tworzenia gniazd w pakiecie UnityVS.

- Naprawiono awarię w programie Visual Studio podczas ładowania obrazów stockowych z zestawów programu Visual Studio.

- Naprawiono błąd w generowaniu UnityVS.VersionSpecific dla kompilacji źródłowych Unity.

- Naprawiono możliwe zamrożenie podczas otwierania gniazda w pakiecie Unity.

- Naprawiono obsługę projektu Unity z myślnikiem (-) w ich nazwie.

- Naprawiono otwieranie skryptów z Unity, aby nie mylić kolejności ALT+TAB dla Unity 4.2 i nowszych.

## <a name="1800"></a>1.8.0.0

Wydana 24 września 2013 r.Released September 24, 2013

### <a name="new-features"></a>Nowe funkcje

- Drastycznie poprawiono szybkość połączenia debugera.

- Automatycznie obsługuje nawigację do pliku i linii w Unity 4.2 i powyżej.

- Warunkowe punkty przerwania.

- Generator plików projektu obsługuje teraz szablony T4.

- Zaktualizuj kreatorów MonBehavior o nowe interfejsy API.

- IntelliSense dokumentacji w języku C# dla typów Unity.

- Ocena wyrażeń arytmetycznych i logicznych.

- Lepsze odnajdowanie zdalnych edytorów dla zdalnego podglądu debugowania.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono błąd, który powodował wyciek wątku w programie VS po odłączeniu debugera.

- Naprawiono biały piksel pojawiający się w programie VS.

- Naprawiono obsługę kliknięć na ikonie paska stanu.

- Naprawiono generowanie odniesień z zestawami w folderach wtyczek.

- Poprawiono tworzenie gniazd z pakietu UnityVS w przypadku wyjątków.

- Naprawiono wykrywanie nowych wersji UnityVS.

- Naprawiono monit menedżera licencji po wygaśnięciu licencji.

- Naprawiono błąd, który mógł spowodować, że lista procesów będzie pusta w debugerze dołączania do przetwarzania okna programu VS.

- Poprawiono zmienianie wartości logicznych w widoku lokalnym.

## <a name="1220"></a>1.2.2.0

Wydana 9 lipca 2013 r.Released July 9, 2013

### <a name="bug-fixes"></a>Poprawki błędów

- Obsługa w pełni kwalifikowanych nazw w oceniający wyrażenia.

- Naprawiono zamrożenie związane z obsługą wyjątków, gdzie aparat skryptów Unity wysyła nam niepoprawne dane stackframe.

- Naprawiono proces kompilacji dla obiektów docelowych sieci Web.

- Naprawiono błąd, który mógł się zdarzyć, jeśli program Visual Studio został uruchomiony i że usunięty plik znajduje się na liście plików do otwarcia podczas uruchamiania.

- Poprawiono UnityVS.OpenFile do obsługi plików innych niż skrypt, takich jak skompilowane shadery.

- Teraz odwołujemy się do Boo.Lang i UnityScript.Lang ze wszystkich projektów C#.

- Poprawiono generowanie odwołań w projektach, jeśli projekt ma znaki specjalne.

- Obejście problemu vs, gdzie wywołanie metody do projektów usuwanych wyzwoliłoby wiele NullReferenceException MessageBox.

- Poprawiono obsługę zestawów beta Unity 4.2.

## <a name="1210"></a>1.2.1.0

Wydana 9 kwietnia 2013 r.Released April 9, 2013

### <a name="bug-fixes"></a>Poprawki błędów

- Poprawiono lokalne wdrażanie zestawów Unity w celu uzupełnienia kodu w przypadku błędu we/wy (takiego jak pliki tylko do odczytu lub pliki zablokowane przez program Visual Studio).

- Naprawiono regresji, gdzie otwarcie skryptu z Unity nie skupić plik, jeśli został już otwarty w programie Visual Studio.

- Naprawiono problem z wydajnością obsługi nowych wyjątków.

- Poprawiono powiązanie punktów przerwania w niektórych zewnętrznych bibliotekach DLL.

## <a name="1200"></a>1.2.0.0

Wydana 25 marca 2013 r.Released March 25, 2013

### <a name="new-features"></a>Nowe funkcje

- Drastycznie poprawiono szybkość połączenia debugera.

- Zoptymalizowany Unity Project Explorer dla większych projektów.

- Honor ustawienia programu Visual Studio do przerwania (lub nie) na obsługiwanych i nieobsługiwał wyjątków.

- Honor visual studio ustawienie wywołać ToString na zmiennych lokalnych.

- Dodaj nowe menu Debug -> Dołącz debuger Unity, którego można użyć do debugowania odtwarzaczy Unity.

- Zachowaj projekty niestandardowe dodane do rozwiązania UnityVS po generowaniu plików rozwiązania.

- Dodaj nowy skrót klawiaturowy CTRL+ALT+M -> CTRL+H, aby wyświetlić dokumentację Unity dla funkcji Unity lub członka w pozycji opiekuna.

- Weź pod uwagę pliki odpowiedzi kompilatora (rsp) podczas kompilowania z programu Visual Studio.

- Dekonstruktor dekonstruktora generowane typy, aby pokazać zmienne podczas debugowania metod generatora.

- Uprość zdalne debugowanie, usuwając konieczność skonfigurowania folderu udostępnionego do unity. Teraz wystarczy mieć dostęp do projektu Unity z systemu Windows.

- Zainstaluj niestandardowy profil Unity jako standardowy profil docelowy .net. To rozwiązuje wszystkie fałszywe alarmy, które może pokazać ReSharper.

- Obejść błąd aparatu skryptów Unity, więc debuger nie pęknie na nie poprawnie zarejestrowanych wątków.

- Przerobić otwieracz plików, aby uniknąć sytuacji wyścigu w VS, gdzie twierdził, że można otworzyć pliki, podczas awarii na żądanie otwarcia pliku.

- UnityVS jest teraz z prośbą, aby odświeżyć kompilacji podczas tworzenia vs projektu, a nie na zapis pliku już.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiliśmy nasz niestandardowy profil .net

- Naprawiono integrację motywów, która rozwiązuje nasze problemy z ciemnym motywem VS 2012.

- Naprawiono skrót szybkiego zachowania w programie VS 2012.

- Naprawiono błąd krokowy, który mógł się zdarzyć, gdy debugowanie i wątek nie-main trafić punkt przerwania.

- Poprawiono zakończenie aliasów typu UnityScript i Boo, takich jak int.

- Naprawiono wyjątek podczas pisania nowego ciągu UnityScript lub Boo.

- Poprawiono wyjątki w menu Unity, gdy rozwiązanie nie zostało załadowane.

- Naprawiono błąd UVS-48: wpisanie podwójnego cudzysłowu czasami powoduje błąd i przerywa wszystkie funkcje (uzupełnianie kodu, podświetlanie składni itp.).

- Naprawiono błąd UVS-46: Zduplikowany otwarty plik skryptu (UnityScript) po kliknięciu na listę błędów programu Visual Studio.

- Naprawiono błąd UVS-42: Logo łączności Unity na pasku stanu nie obsługuje zdarzeń myszy w programie VS 2012.

- Naprawiono błąd UVS-44: CTRL +SHIFT+Q nie jest dostępny w VS 2012 dla szybkich monobezachów.

- Naprawiono błąd UVS-40: Wybrane elementy w Eksploratorze projektu Unity są nieczytelne, gdy okno jest nieaktywne w "ciemnym" motywie VS2012.

- Naprawiono błąd UVS-39: Problem tokenizacji uciekł ciągi.

- Naprawiono błąd UVS-35: Wywołaj ToString na obiektach podczas sprawdzania zmiennych.

- Naprawiono błąd UVS-27: Niespójność okna Goto Symbol z "ciemnym" motywem w VS2012.

- Naprawiono błąd UVS-11: Miejscowi w coroutines.

## <a name="1100---beta-release"></a>1.1.0.0 - Wersja beta
Wydano 9 marca 2013 r.

## <a name="10130"></a>1.0.13.0
Wydana 21 stycznia 2013 r.Released January 21, 2013

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono blokady programu Visual Studio, które może się zdarzyć, jeśli debuggee docelowe wysyła nieprawidłowe zdarzenia wątku. To zwykle zdarza się podczas debugowania zdalnego Unity na OSX.

- Naprawiono blokadę programu Visual Studio, która może się zdarzyć, jeśli wyjątek zostanie zamknięty debuger.

- Naprawiono nasze pomocników MonoBehavior, gdy C# MonoBehavior znajduje się w przestrzeni nazw.

- Poprawiono etykietki narzędzi debugera dla języka UnityScript w programie Visual Studio 2012.

- Poprawiono generowanie projektu, gdy tylko stałe debugowania są zmieniane z Unity.

- Poprawiono nawigację za pomocą klawiatury w Eksploratorze projektu Unity.

- Poprawiono kolorowanie UnityScript dla ciągów wysuń.

- Naprawiono nasz otwieracz plików, aby lepiej odgadnąć nazwę projektu, gdy jest używany poza Unity. Jest to konieczne, gdy użytkownik używa trzeciego otwieracza plików części w Unity, który deleguje do UnityVS.

- Naprawiono obsługę długich wiadomości wysyłanych z Unity do UnityVS. Wcześniej długie wiadomości mogą spowodować awarię naszej części wiadomości UnityVS. W konsekwencji czasami UnityVS nie otworzy pliku z Unity.

## <a name="10120"></a>1.0.12.0
Wydano 3 stycznia 2013 r.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono blokadę programu Visual Studio, która mogła się zdarzyć, gdy program Visual Studio usuwał punkt przerwania.

- Naprawiono błąd, który powodował, że niektóre punkty przerwania nie były trafiane po ponownym skompilowanym skryptach gry Unity.

- Naprawiono debuger poprawnie powiadamiać Visual Studio, gdy punkty przerwania były niezwiązane.

- Rozwiązano problem z rejestracją, który mógł uniemożliwiać debugerowi programu Visual Studio debugowanie programów natywnych.

- Naprawiono wyjątek, który mógł się zdarzyć podczas oceny wyrażeń UnityScript i Boo.

- Naprawiono regresję, w której zmiana poziomu interfejsu API .net w unity nie wyzwoliła aktualizacji plików projektu.

- Naprawiono błąd interfejsu API, w którym kod użytkownika nie mógł uczestniczyć w programie obsługi wywołania zwrotnego dziennika.

## <a name="10110"></a>1.0.11.0
Wydana 28 listopada 2012 r.Released November 28, 2012

### <a name="new-features"></a>Nowe funkcje

- Oficjalne wsparcie Unity 4.

- Manipulowanie skryptami z Eksploratora projektu Unity.

- Integracja w oknie Przejdź do programu Visual Studio.

- Analizowanie komunikatu konsoli informacji, tak aby kliknięcie na liście błędów przekierowywać do pierwszego stackframe z symbolami.

- Dodaj [interfejs API,](../cross-platform/customize-project-files-created-by-vstu.md) aby umożliwić użytkownikowi udział w generowaniu projektu.

- Dodaj [interfejs API,](../cross-platform/share-the-unity-log-callback-with-vstu.md) aby umożliwić użytkownikowi udział w LogCallback.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono regresję w tle Eksploratora projektu Unity w programie Visual Studio 2012.

- Poprawiono generowanie projektu dla użytkowników pełnego profilu .net.

- Poprawiono generowanie projektu dla użytkowników obiektu docelowego sieci Web.

- Poprawiono generowanie projektu, aby uwzględnić symbole kompilacji DEBUG i TRACE, tak jak unity.

- Naprawiono awarię podczas używania znaków specjalnych w naszym oknie Symbol Goto.

- Naprawiono awarię, jeśli nie możemy wstrzyknąć naszej ikony na pasku stanu programu Visual Studio.

## <a name="10100"></a>1.0.10.0
Wydana 9 października 2012 r.Released October 9, 2012

### <a name="bug-fixes"></a>Poprawki błędów

- Poprawiono tło Eksploratora projektu Unity w programie Visual Studio 2010.

- Naprawiono zamrożenie programu Visual Studio, które może się zdarzyć, jeśli UnityVS próbował dołączyć debuger do Unity, którego interfejs debugera wcześniej rozbił.

- Naprawiono zamrożenie programu Visual Studio, które mogło się zdarzyć, gdy punkt przerwania został ustawiony i nastąpi ponowne załadowanie AppDomain.

- Naprawiono sposób, w jaki zestawy są pobierane z Unity, aby uniknąć blokowania plików i mylić proces kompilacji Unity.

## <a name="1090"></a>1.0.9.0

Wydana 3 października 2012 r.Released October 3, 2012

### <a name="bug-fixes"></a>Poprawki błędów

- Poprawiono generowanie projektu, gdy projekt Unity zawiera rzeczywiste zasoby JavaScript.

- Naprawiono obsługę błędów w ocenie wyrażeń.

- Poprawiono ustawianie nowych wartości dla pól typów wartości.

- Naprawiono możliwe skutki uboczne podczas najeżdżania kursorem na wyrażenia z edytora kodu.

- Poprawiono sposób wyszukiwania typów w załadowanych zestawach do oceny wyrażenia.

- Naprawiono błąd UVS-21: Ocena przypisania obiektów Unity nie ma wpływu.

- Naprawiono błąd UVS-21: Nieprawidłowy wskaźnik podczas oceny wywołania metody do interfejsu API matematyki Unity.

## <a name="1080"></a>1.0.8.0

Wydana 26 września 2012 r.Released September 26, 2012

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono sposób, w jaki nasz otwieracz skryptów nabył ścieżkę do projektu, aby upewnić się, że jest w stanie otworzyć zarówno visual studio, jak i skrypty.

- Naprawiono błąd z punktami przerwania utworzonymi podczas uruchamiania sesji debugowania, który mógł spowodować zablokowanie programu Visual Studio.

- Poprawiono sposób rejestracji unityvs w programie Visual Studio 2010.

## <a name="1070"></a>1.0.7.0

Wydana 14 września 2012 r.Released September 14, 2012

### <a name="new-features"></a>Nowe funkcje

- Pomoc techniczna programu Visual Studio 2012.

### <a name="bug-fixes"></a>Poprawki błędów

- Poprawiono generowanie plików projektu edytora i wtyczek, aby dopasować zachowanie Unity.

- Naprawiono tłumaczenie symboli .pdb na Unity 4.

> [!IMPORTANT]
> Ze względu na pomoc techniczną programu Visual Studio 2012 musieliśmy zmienić nazwę kilku plików i przenieść inne pliki. Pakiet UnityVS do importowania Unity jest teraz nazwany UnityVS 2010 lub UnityVS 2012, odpowiednio visual studio 2010 i Visual Studio 2012. Ta wersja wymaga również, że pliki projektu UnityVS są regenerowane.

## <a name="1060---internal-build"></a>1.0.6.0 - Kompilacja wewnętrzna
Wydana 12 września 2012 r.Released September 12, 2012

## <a name="1050"></a>1.0.5.0

Wydana 10 września 2012

### <a name="bug-fixes"></a>Poprawki błędów

- Poprawiono generowanie plików projektu, gdy skrypty lub moduły cieniowania miały nieprawidłowy znak xml.

- Poprawiono wykrywanie wystąpień Unity, gdy Unity był podłączony do serwera zasobów. Spowoduje to błędy otwierania plików z unity i automatyczne połączenie debugera programu Visual Studio.

## <a name="1040"></a>1.0.4.0

Wydana 5 września 2012 r.

### <a name="new-features"></a>Nowe funkcje

- Automatyczna konwersja symboli debugowania w Unity.

    Jeśli masz .NET .dll zestawu z jego skojarzone .pdb w folderze zasobów, po prostu ponownie zaimportować zestaw i UnityVS przekonwertuje .pdb do pliku symboli debugowania, że aparat skryptów Unity rozumie, i będziesz mógł wkroczyć do .NET zestawów z Unityvs.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono awarię UnityVS podczas debugowania spowodowane przez wyjątki generowane przez metody lub właściwości wewnątrz Unity.

## <a name="1030"></a>1.0.3.0

Wydana 4 września 2012 r.Released September 4, 2012

### <a name="new-features"></a>Nowe funkcje

- Nowa opcja konfiguracji, aby wyłączyć użycie UnityVS do otwierania plików z Unity.

### <a name="bug-fixes"></a>Poprawki błędów

- Poprawiono generowanie odniesień do UnityEditor dla projektów nieredaktorowych.

- Poprawiono definicję symbolu UNITY_EDITOR dla projektów niebędących edytorami.

- Naprawiono losową awarię VS spowodowaną przez nasz niestandardowy pasek stanu.

## <a name="1020"></a>1.0.2.0

Wydana 30 sierpnia 2012 r.Released August 30, 2012

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono konflikt z debugerem PythonTools.

- Poprawiono odniesienia do Mono.Cecil.

- Naprawiono błąd w sposobie pobierania zestawów skryptów z Unity with Unity 4 b7.

## <a name="1010"></a>1.0.1.0

Wydana 28 sierpnia 2012 r.Released August 28, 2012

### <a name="new-features"></a>Nowe funkcje

- Obsługa podglądu dla unity 4.0 beta.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono inspekcję właściwości zgłaszających wyjątki.

- Naprawiono malejąco do obiektów bazowych podczas sprawdzania obiektów.

- Naprawiono pustą listę rozwijanej punktu wstawiania w kreatorze MonoBehavior.

- Poprawiono uzupełnianie biblioteki DLL w folderze Zasoby dla UnityScript i Boo.

## <a name="1000---initial-release"></a>1.0.0.0 - Wydanie początkowe
Wydana 22 sierpnia 2012 r.Released August 22, 2012
