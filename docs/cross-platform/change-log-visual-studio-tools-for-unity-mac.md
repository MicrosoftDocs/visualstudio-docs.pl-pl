---
title: Dziennik zmian (Narzędzia programu Visual Studio dla unity, Mac) | Dokumenty firmy Microsoft
ms.custom: ''
ms.date: 12/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 5599153f79b273249e93c48aaa197214d92f5fe7
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232916"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Dziennik zmian (narzędzia Visual Studio Tools for Unity, komputery Mac)

Visual Studio Narzędzia dla dziennika zmian Unity.

## <a name="2520"></a>2.5.2.0

Wydano 23 marca 2020 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Poprawiono rejestrację wątków po dołączeniu.

## <a name="2510"></a>2.5.1.0

Wydano 3 marca 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano tłumik [`IDE0051`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0008.md)dla . Prywatne metody używane z Invoke, InvokeRepeating, StartCoroutine lub StopCoroutine nie powinny być oznaczone jako nieużywane.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Poprawiono ondrawgizmos/ondrawgizmosWybrana dokumentacja

- **Oceny:**

  - Poprawiono kontrolę argumentów lambda.

## <a name="2501"></a>2.5.0.1

Wydana 19 lutego 2020 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Poprawiono [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0006.md) sprawdzanie diagnostyczne pod kątem nieprawidłowego podpisu wiadomości. Podczas sprawdzania typów z wieloma poziomami dziedziczenia ta `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added`diagnostyka może zakończyć się niepowodzeniem, korzystając z następującego komunikatu: .

## <a name="2500"></a>2.5.0.0

Wydano 22 stycznia 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę plików HLSL.
  
  - Przełączony do nowego interfejsu użytkownika okna dialogowego folderu.
  
  - Przełączony do nowej siatki właściwości dostępne dla ustawień.

  - Dodano tłumik [`IDE0051`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0006.md)dla . Pola prywatne `SerializeField` z atrybutem nie powinny być oznaczane jako nieużywane.

  - Dodano tłumik [`CS0649`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0007.md)dla . Pola z `SerializeField` atrybutem nie powinny być oznaczone jako nieprzypisane.  

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Stałe generowanie`GenerateTargetFrameworkMonikerAttribute` projektu (cel nie zawsze znajdował się poprawnie)

- **Oceny:**

  - Poprawiono ocenę ciągu (nie używanie wywołań ToString()

## <a name="2420"></a>2.4.2.0

Wydano 3 grudnia 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Poprawiono diagnostykę z interfejsami zdefiniowanymi przez użytkownika.

  - Naprawiono szybkie etykietki narzędzi z zniekształconych wyrażeń.
  
## <a name="2410"></a>2.4.1.0

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

## <a name="2400"></a>2.4.0.0

Wydano 15 października 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano tłumik `IDE0060` dla (nieużywany parametr) dla wszystkich komunikatów Unity.

  - Dodano szybką etykietkę narzędzia dla `TooltipAttribute`pól oznaczonych tagiem . (To będzie działać na prosty uzyskać akcesor za pomocą tego pola, jak również).

## <a name="2330"></a>2.3.3.0

Wydano 23 września 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano nowy tłumik ide0060, aby zapobiec IDE z pokazano quick-fix, aby usunąć nieużywane parametry.
    - `USP0005`for: `IDE0060`Unity komunikaty są wywoływane przez środowisko uruchomieniowe Unity.

## <a name="2320"></a>2.3.2.0

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

## <a name="2310"></a>2.3.1.0

Wydano 4 września 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Oceny:**

  - Dodano obsługę lepszego wyświetlania typu, `List<object>` czyli `List'1[[System.Object, <corlib...>]]`zamiast .

  - Dodano obsługę dostępu do elementu członkowskiego `p->data->member`wskaźnika, tj.

  - Dodano obsługę niejawnych konwersji w inicjatorach tablicowych, tj. `new byte [] {1,2,3,4}`

  - Dodano obsługę edytora szesnastków podczas sprawdzania tablic i ciągów bajtów.

## <a name="2300"></a>2.3.0.0

Wydano 13 sierpnia 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oceny:**

  - Naprawiono problemy z przechodzeniem na przechodzenie z wyjątkami.

  - Poprawiono ocenę pseudo identyfikatorów (takich jak $exception).

  - Zapobiegaj awarii podczas dereferencji nieprawidłowych adresów.  

  - Naprawiono błąd z niezaładowanych appdomains.

## <a name="2200"></a>2.2.0.0

Wydano 25 lipca 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oceny:**

  - Poprawiono kontrolę z typami IntPtr.

- **Debuger:**

  - Poprawiono obsługę punktów połowowych i punktów przerwania funkcji.

## <a name="2130"></a>2.1.3.0

Wydano 9 lipca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Dodano obsługę łapania podklas wyjątków.

  - Dodano obsługę protokołu MDS 2.51.

- **Integracji:**

  - Dodano obsługę plików asmdef.

  - Przełącz się do trybu zmiany nazwy, gdy plik jest dodawany z szablonu (aby naśladować zachowanie Edytora Unity).

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono obsługę nieprawidłowo sformułowanych wiadomości podczas komunikowania się z graczami Unity.

- **Oceny:**

  - Poprawiono obsługę obszarów nazw w wyrażeniach.

## <a name="2120"></a>2.1.2.0

Wydano 2 lipca 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oceny:**

  - Naprawiono raportowanie błędów przy obliczania niesparowalnych.

## <a name="2110"></a>2.1.1.0

Wydano 27 czerwca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Zaktualizowano interfejs API monobehaviour do wersji 2019.1.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Poprawiono wydajność Eksploratora projektów Unity.

  - Naprawiono ostrzeżenia raportowania i błędy do wyjścia, gdy włączona jest lekka kompilacja.

  - Poprawiono lekkość wykonania.

## <a name="2100"></a>2.1.0.0

Wydano 20 czerwca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Wyłączone pełnej kompilacji dla projektów Unity, na rzecz korzystania z błędów IntelliSense i ostrzeżenia. Rzeczywiście Unity tworzy rozwiązanie Visual Studio z projektów biblioteki klas, które reprezentują, co Unity robi wewnętrznie. Mając na uwadze, że wynik kompilacji w programie Visual Studio nigdy nie jest używany lub odbierane przez Unity jako ich potok kompilacji jest zamknięty. Tworzenie w programie Visual Studio jest po prostu zużywa zasoby za darmo. Jeśli potrzebujesz pełnej kompilacji, ponieważ masz narzędzia lub konfigurację, która zależy od niego, można wyłączyć tę optymalizację (Ustawienia/Narzędzia dla Unity/Wyłącz pełną kompilację projektów).
  
  - Dodano obsługę pakietów Unity w UPE. Widoczne są tylko pakiety odniesienia (przy użyciu manifest.json w folderze) `Packages` i pakiety lokalne (osadzone w folderze). `Packages`

## <a name="2021"></a>2.0.2.1

Wydano 30 maja 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano niestandardową ikonę celów wykonania Jedności.

## <a name="2020"></a>2.0.2.0

Wydano 2 kwietnia 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę automatycznego odświeżania bazy danych zasobów Unity przy zapisywaniu. Jest to domyślnie włączone i wyzwoli ponowną kompilację po stronie Unity podczas zapisywania skryptu w programie Visual Studio. Tę funkcję można wyłączyć w obszarze Narzędzia\Opcje\Narzędzia dla unity\Refresh Unity's AssetDatabase przy zapisywaniu.

  - Dodano obsługę ustawiania preferowanej instalacji unity dla dokumentacji w trybie offline.

  - Dodano menu kontekstowe dla nowego edytora.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Poprawiono filtrowanie montażu i kontrolę ramy z pustymi ramkami.

## <a name="2011"></a>2.0.1.1
 
 Wydano 26 marca 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Tymczasowo ustaw mono jako domyślny i tylko użyteczny debuger dla tej bardzo konkretnej wersji.

## <a name="2006"></a>2.0.0.6

Wydano 26 marca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę "Dołącz do jedności i graj".

## <a name="2005"></a>2.0.0.5

Wydano 20 marca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Zachowaj właściwości zewnętrzne podczas przetwarzania pliku rozwiązania.
  
- **Oceny:**

  - Dodano obsługę nazw kwalifikowanych aliasem (na razie tylko globalna przestrzeń nazw). Tak więc oceniający wyrażenie jest teraz akceptowanie typów przy użyciu formularza global::namespace.type.

  - Dodano obsługę `pointer[index]` formularza, który jest semantycznie `*(pointer+index)` identyczny z formą wyłuskania wskaźnika.

## <a name="2004"></a>2.0.0.4

Wydano 5 marca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Zaktualizowano `ScriptableObject` interfejs API.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Usunięto obszary nazw z szablonów.

## <a name="2003"></a>2.0.0.3
 
 Wydano 5 marca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Pola publiczne i serializowane nie będą już powodować ostrzeżeń. Mamy automatycznie pomijane `CS0649` ostrzeżenia `IDE0051` i kompilatora w projektach Unity, które utworzyły te komunikaty.

- **Integracji:**

  - Monit o dołączenie do określonego wystąpienia, jeśli więcej, że jeden proces Unity jest uruchomiony.

- **Oceny:**

  - Dodano obsługę funkcji lokalnych.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Poprawiono odczytywanie atrybutu niestandardowego na nazwanych argumentów podczas korzystania ze starych wersji protokołu.

## <a name="2002"></a>2.0.0.2

Wydano 4 lutego 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Zaktualizowano interfejs API monobehaviour.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Poprawiono ustawienie wartości pierwotnych w debugerze.

## <a name="2001"></a>2.0.0.1

Wydano 4 grudnia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Stały pakiet instalacyjny samowystarczalny.

## <a name="2000"></a>2.0.0.0
 Wydano 4 grudnia 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Zastąpiono debuger Unity na komputerze Mac tym samym rdzeniem debuger Unity z systemu Windows.

  - Zastąpiono NRefactory na rzecz Roslyn do oceny wyrażenia.

  - Dodano obsługę wskaźników: wyłuskanie, rzutowanie i arytmetyka wskaźnika (w tym celu wymagane są zarówno Unity 2018.2+, jak i nowe środowisko wykonawcze).

  - Dodano obsługę widoku wskaźnika tablicy (jak w języku C++). Weź wyrażenie wskaźnika, a następnie dołącz przecinek i liczbę elementów, które chcesz zobaczyć.

  - Dodano obsługę konstrukcji asynchronii.

  - Dodano obsługę pseudo zmiennych (identyfikatory wyjątków i obiektów).

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Poprawiono ocenę wyrażenia z nieprawidłowo sformułowanych lub nieobsługiwałych wyrażeń.

## <a name="1700"></a>1.7.0.0

Wydano 13 listopada 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Dodano więcej informacji o kliencie (IP, nazwa komputera) w oknie dialogowym dołączania.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono zakleszczenie w bibliotece używane do komunikowania się z aparatem debugera Unity, co spowodowało zamrożenie programu Visual Studio lub Unity, szczególnie podczas uderzania "Dołącz do jedności" lub ponownego uruchamiania gry.

- **Integracji:**

  - Naprawiono aktywację wtyczki Unity, gdy wybrano inny domyślny edytor.

  - Poprawiono tworzenie szablonu pliku Unity.

## <a name="1602"></a>1.6.0.2

Wydana 24 lipca 2018 r.Released July 24, 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Wycofane obejście problemu wydajności Unity, który został naprawiony przez Unity.

## <a name="1601"></a>1.6.0.1

Wydano 10 lipca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Poprawiono obsługę zabarwienia kodu modułu cieniującego.

## <a name="1600"></a>1.6.0.0

Wydana 26 czerwca 2018 r.Released June 26, 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Kreatorów:**

  - Poprawiono literówkę z komunikatem OnApplicationFocus.

- **Generowanie projektu:**

  - Obejście przejściowe dla błędu wydajności Unity: pamięć podręczna MonoIslands podczas generowania projektów.

  - Nie należy już konwertować przenośnej pdb do mdb podczas korzystania z nowego środowiska wykonawczego Unity.

## <a name="1502"></a>1.5.0.2

Wydana 18 kwietnia 2018 r.Released April 18, 2018

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę podstawowego uzupełniania kodu modułu cieniującego.

  - Dodano obsługę przełączania komentarzy w plikach shader.

## <a name="1501"></a>1.5.0.1

Wydana 28 marca 2018 r.Released March 28, 2018

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę dodatkowych szablonów w Eksploratorze projektów Unity.

## <a name="1500"></a>1.5.0.0

Wydano 21 marca 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę wykrywania i podłączania do odtwarzaczy Android podłączonych przez USB.

## <a name="1403"></a>1.4.0.3

Wydano 5 marca 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano wsparcie dla nowego generatora projektów w Unity 2018.1.

- **Integracji:**

  - Dodano panel opcji dla ustawień dedykowanych.

## <a name="1402"></a>1.4.0.2

Wydano 24 stycznia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono wykrywanie wersji mono.

- **Integracji:**

  - Naprawiono problemy z pomiarem czasu z 2018.1 i aktywacją wtyczki.

  - Naprawiono powiadomienia podczas wykrywania nowego gracza.

## <a name="1401"></a>1.4.0.1

Wydano 23 stycznia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Poprawiono rozwijanie/zwijanie folderów po dwukrotnym kliknięciu

## <a name="1400"></a>1.4.0.0

Wydano 13 grudnia 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę standardu .NET.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono automatyczną konwersję symboli debugowania pdb do mdb.

## <a name="1301"></a>1.3.0.1

Wydano 12 grudnia 2017 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono pośrednie wywołanie EditorPrefs.GetBool wpływ inspektora podczas próby zmiany rozmiaru tablicy.

- **Kreatorów:**

  - Odśwież kontekst roslyn przed wstawieniem metody.

## <a name="1300"></a>1.3.0.0

Wydana 20 listopada 2017 r.Released November 20, 2017

### <a name="new-features"></a>Nowe funkcje

- **Kreatorów:**

  - Dodano kreatora "Implementuj komunikat Unity".

  - Dodano obsługę nowego interfejsu API ukończenia w programie VS dla komputerów Mac 7.4.

## <a name="1200"></a>1.2.0.0

Wydana 23 października 2017 r.Released October 23, 2017

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Dodano obsługę przenośnych plików symboli debugowania.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono dodatkowe rozszerzenie dll niesłusznie dodane do nazwy pliku złożenia.

  - Nie wymuszaj AllowAttachedDebuggingOfEditor Unity flagi jako domyślne jest teraz "true".

## <a name="1103"></a>1.1.0.3

Wydana 23 października 2017 r.Released October 23, 2017

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę profilu .NET 4.6.

## <a name="1102"></a>1.1.0.2

Wydana 8 sierpnia 2017 r.Released August 8, 2017

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Uruchom okno dialogowe dołączania do procesu, jeśli nie wiesz, do której funkcji Unity dołączyć.

- **Generowanie projektu:**

  - Zawsze włączaj niebezpieczny przełącznik kompilacji, gdy używana jest unity 5.6.

## <a name="1101"></a>1.1.0.1

Wydana 20 lipca 2017 r.Released July 20, 2017

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę zlokalizowanych zasobów.

## <a name="1100"></a>1.1.0.0

Wydano 12 lipca 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę dołączania do graczy i redaktorów za pośrednictwem okna Dołącz do procesu.

- **Generowanie projektu:**

  - Poprawiono odwołania do nazw zestawu za pomocą plików mcs.rsp.

  - Dodano obsługę jednostek kompilacji assembly.json.

  - Poprawiono definicje z poziomami INTERFEJSU API.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono komunikat o błędzie modułu cieniującego podczas kompilowania.

## <a name="1001"></a>1.0.0.1

Wydana 4 maja 2017 r.Released May 4, 2017

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Poprawiono aktywne śledzenie dokumentów za pomocą projektów hybrydowych i zwykłych.

## <a name="1000"></a>1.0.0.0

Wydana 3 maja 2017 r.Released May 3, 2017
