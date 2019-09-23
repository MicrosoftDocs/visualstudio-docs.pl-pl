---
title: Zmienianie dziennika (Visual Studio Tools for Unity, komputery Mac) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/18/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 897851055bd2eacc10edea9fdff2ab3ecd61b963
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71185961"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Dziennik zmian (narzędzia Visual Studio Tools for Unity, komputery Mac)

Dziennik zmian w programie Visual Studio Tools for Unity.

## <a name="2330"></a>2.3.3.0

Wydanie 23 września, 2019

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Dodano nowy element do pomijania dla IDE0060, aby zapobiec wyświetlaniu przez środowisko IDE szybkiej naprawy w celu usunięcia nieużywanych parametrów.
    - `USP0005`dla `IDE0060`: Komunikaty aparatu Unity są wywoływane przez środowisko uruchomieniowe aparatu Unity.

## <a name="2320"></a>2.3.2.0

Wydanie 16 września 2019

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Wyjaśniono, że program Visual Studio obsługuje projekty Unity przez dodanie nowej diagnostyki specyficznej dla aparatu Unity. Wprowadziliśmy również zmiany powodujące, że środowisko IDE działa teraz bardziej inteligentnie dzięki pomijaniu ogólnej diagnostyki języka C#, która nie dotyczy projektów Unity. Na przykład IDE nie będzie wyświetlał szybkiej poprawki, aby zmienić zmienną inspektora, do `readonly` której nie można zmodyfikować zmiennej w edytorze aparatu Unity.
    - `UNT0001`: Komunikaty aparatu Unity są wywoływane przez środowisko uruchomieniowe, nawet jeśli są puste. Nie deklaruj ich, aby uniknąć wykonywania zbędnego przetwarzania przez środowisko uruchomieniowe aparatu Unity.
    - `UNT0002`: Porównanie tagów przy użyciu równości ciągów jest wolniejsze niż wbudowana metoda CompareTag.
    - `UNT0003`: Użycie generycznej formy metody GetComponent jest preferowane ze względu na bezpieczeństwo typu.
    - `UNT0004`: Komunikat Update jest zależny od szybkości ramki i powinien używać wartości Time.deltaTime, a nie wartości Time.fixedDeltaTime.
    - `UNT0005`: Komunikat FixedUpdate jest niezależny od szybkości ramki i powinien używać wartości Time.fixedDeltaTime, a nie wartości Time.deltaTime.
    - `UNT0006`: Wykryto niepoprawną sygnaturę metody dla tego komunikatu aparatu Unity.
    - `UNT0007`: Aparat Unity przesłania wartość operatora porównania null dla obiektów Unity, które są niezgodne z łączeniem wartości null.
    - `UNT0008`: Aparat Unity przesłania wartość operatora porównania null dla obiektów Unity, które są niezgodne z propagacją wartości null.
    - `UNT0009`: Podczas stosowania atrybutu InitializeOnLoad względem klasy należy podać konstruktor statyczny. Atrybut InitializeOnLoad zapewnia, że zostanie on wywołany podczas uruchamiania edytora.
    - `UNT0010`: Składniki MonoBehaviour powinny być tworzone tylko za pomocą metody AddComponent(). MonoBehaviour to składnik, który musi zostać dołączony do obiektu GameObject.
    - `UNT0011`: Składniki ScriptableObject powinny być tworzone tylko za pomocą metody CreateInstance(). Obiekt ScriptableObject musi zostać utworzony przez aparat Unity do obsługi metod komunikatów aparatu Unity.
    - `USP0001`dla `IDE0029`: Obiekty Unity nie powinny używać łączenia o wartości null.
    - `USP0002`dla `IDE0031`: Obiekty Unity nie powinny używać propagacji wartości null.
    - `USP0003`dla `IDE0051`: Komunikaty aparatu Unity są wywoływane przez środowisko uruchomieniowe aparatu Unity.
    - `USP0004`dla `IDE0044`: Pola z atrybutem SerializeField nie powinny być tylko do odczytu.

## <a name="2310"></a>2.3.1.0

wydanie 4 września 2019

### <a name="new-features"></a>Nowe funkcje

- **Ocena:**

  - Dodano obsługę wyświetlania lepszych typów, tj. `List<object>` `List'1[[System.Object, <corlib...>]]`zamiast.

  - Dodano obsługę dostępu do elementu członkowskiego wskaźnika, `p->data->member`tj.

  - Dodano obsługę niejawnych konwersji w inicjatorach tablicy, tj `new byte [] {1,2,3,4}`.

  - Dodano obsługę edytora szesnastkowego podczas sprawdzania tablic bajtowych i ciągów.

## <a name="2300"></a>2.3.0.0

Opublikowano 13 sierpnia 2019

### <a name="bug-fixes"></a>Poprawki błędów

- **Ocena:**

  - Rozwiązywanie problemów z wyjątkami.

  - Stała Ocena identyfikatorów pseudo (takich jak $exception).

  - Zapobiegaj awarii podczas usuwania odwołań do nieprawidłowych adresów.  

  - Rozwiązano problem z niezaładowanymi domenami aplikacji.

## <a name="2200"></a>2.2.0.0

Wydana 25 lipca 2019

### <a name="bug-fixes"></a>Poprawki błędów

- **Ocena:**

  - Stała Inspekcja przy użyciu typów IntPtr.

- **Debuger:**

  - Stała obsługa catchpoints i punktów przerwania funkcji.

## <a name="2130"></a>2.1.3.0

wydanie 9 lipca 2019

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Dodano obsługę przechwytywania podklas wyjątków.

  - Dodano obsługę protokołu MDS 2,51.

- **Integracja:**

  - Dodano obsługę plików asmdef.

  - Przełącz do trybu zmiany nazwy, gdy plik zostanie dodany z szablonu (aby naśladować zachowanie edytora Unity).

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

  - Stała obsługa nieprawidłowych komunikatów podczas komunikowania się z graczami aparatu Unity.

- **Ocena:**

  - Stała obsługa przestrzeni nazw w wyrażeniach.

## <a name="2120"></a>2.1.2.0

wydanie 2 lipca 2019

### <a name="bug-fixes"></a>Poprawki błędów

- **Ocena:**

  - Naprawiono raportowanie błędów z wyrażeniami niemożliwymi do przeanalizowania.

## <a name="2110"></a>2.1.1.0

Wydana 27 czerwca 2019

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Zaktualizowano interfejs API o bezzachowań do 2019,1.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

  - Stała wydajność Eksploratora projektów środowiska Unity.

  - Naprawiono ostrzeżenia i błędy raportowane w przypadku włączenia uproszczonej kompilacji.

  - Stała wydajność lekkiej kompilacji.

## <a name="2100"></a>2.1.0.0

Wydana 20 czerwca 2019

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Wyłączono pełną kompilację dla projektów środowiska Unity, na korzyść używania błędów i ostrzeżeń funkcji IntelliSense. Istotny aparat Unity tworzy rozwiązanie programu Visual Studio z projektami biblioteki klas, które reprezentują, co Unity działa wewnętrznie. Z tego powodu wynik kompilacji w programie Visual Studio nigdy nie jest używany lub nie jest wybierany przez środowisko Unity, ponieważ ich potok kompilacji jest zamknięty. Kompilowanie w programie Visual Studio jest samo zużywanie zasobów. Jeśli potrzebujesz pełnej kompilacji, ponieważ masz narzędzia lub Instalatora, które od niego zależą, możesz wyłączyć tę optymalizację (ustawienia/narzędzia dla aparatu Unity/wyłączyć pełną kompilację projektów).
  
  - Dodano obsługę pakietów Unity w UPE. Widoczne są tylko pakiety, do których istnieją odwołania ( `Packages` przy użyciu manifest. JSON w folderze) i `Packages` pakiety lokalne (osadzone w folderze).

## <a name="2021"></a>2.0.2.1

Wydana 30 maja 2019

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Dodano niestandardową ikonę dla celów wykonywania środowiska Unity.

## <a name="2020"></a>2.0.2.0

Wydanie 2 kwietnia 2019

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Dodano obsługę automatycznego odświeżania bazy danych zasobów aparatu Unity przy zapisywaniu. Ta funkcja jest domyślnie włączona i wyzwala ponowną kompilację po stronie aparatu Unity podczas zapisywania skryptu w programie Visual Studio. Tę funkcję można wyłączyć w programie Tools\Options\Tools for Unity\Refresh Unity AssetDatabase przy zapisywaniu.

  - Dodano obsługę ustawiania preferowanej instalacji aparatu Unity dla dokumentacji w trybie offline.

  - Dodano menu kontekstowe dla nowego edytora.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Stałe filtrowanie zestawów i inspekcja ramek z pustymi ramkami.

## <a name="2011"></a>2.0.1.1
 
 Wydana 26 marca 2019

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

  - Tymczasowo Ustaw mono jako domyślny i możliwy do użycia debuger dla tej bardzo konkretnej wersji.

## <a name="2006"></a>2.0.0.6

Wydana 26 marca 2019

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Dodano obsługę funkcji "Dołącz do środowiska Unity i Play".

## <a name="2005"></a>2.0.0.5

Wydana 20 marca 2019

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Zachowaj właściwości zewnętrzne podczas przetwarzania pliku rozwiązania.
  
- **Ocena:**

  - Dodano obsługę nazw kwalifikowanych aliasem (tylko globalna przestrzeń nazw dla teraz). Dlatego ewaluatora wyrażeń akceptuje teraz typy przy użyciu formularza Global:: Namespace. Type.

  - Dodano obsługę `pointer[index]` formularza, która jest semantycznie identyczna z formularzem dereferencji `*(pointer+index)` wskaźnika.

## <a name="2004"></a>2.0.0.4

Wydana 5 marca 2019

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Zaktualizowano `ScriptableObject` interfejs API.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

  - Usunięto przestrzenie nazw z szablonów.

## <a name="2003"></a>2.0.0.3
 
 Wydana 5 marca 2019

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Pola publiczne i serializowane nie będą już powodowały ostrzeżeń. W projektach Unity, które utworzyły `CS0649` te `IDE0051` komunikaty, zostały pominięte ostrzeżenia kompilatora.

- **Integracja:**

  - Monituj o dołączenie do określonego wystąpienia, jeśli więcej niż jeden proces Unity jest uruchomiony.

- **Ocena:**

  - Dodano obsługę funkcji lokalnych.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Stały odczyt atrybutu niestandardowego dla nazwanych argumentów w przypadku używania starych wersji protokołu.

## <a name="2002"></a>2.0.0.2

Wydana 4 lutego 2019

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Zaktualizowano interfejs API z zachowaniem.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono wartości pierwotne w debugerze.

## <a name="2001"></a>2.0.0.1

Wydanie 4 grudnia 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

  - Stałe zawiera samodzielne pakiety instalacji.

## <a name="2000"></a>2.0.0.0
 Wydanie 4 grudnia 2018

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Zamieniono debuger Unity na komputerze Mac z tym samym debugerem podstawowego aparatu Unity z systemu Windows.

  - Zamieniono NRefactory na korzyść Roslyn na potrzeby oceny wyrażenia.

  - Dodano obsługę wskaźników: dereferencja, rzutowania lub arytmetycznego wskaźnika (w tym celu wymagane są zarówno środowisko Unity 2018.2 + i nowe środowisko uruchomieniowe).

  - Dodano obsługę widoku wskaźnika tablicy (jak w programie C++). Wypełnij wyrażenie wskaźnika, a następnie Dołącz przecinek i liczbę elementów, które chcesz zobaczyć.

  - Dodano obsługę konstrukcji asynchronicznych.

  - Dodano obsługę pseudo zmiennych (wyjątków i identyfikatorów obiektów).

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Obliczanie stałych wyrażeń z nieprawidłowo sformułowanymi lub nieobsługiwanymi wyrażeniami.

## <a name="1700"></a>1.7.0.0

Wydana 13 listopada 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - W oknie dialogowym Dołącz, należy dodać więcej informacje o kliencie (adresu IP, nazwy komputera).

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono zakleszczenie w bibliotece, używany do komunikacji z aparatem debugera mechanizmu Unity, dzięki czemu program Visual Studio lub Unity, blokowanie, szczególnie w przypadku osiągnięcia "Dołącz do aparatu Unity" lub ponownego uruchamiania gry.

- **Integracja:**

  - Naprawiono Unity wtyczki aktywacji wybranie innego domyślnego edytora.

  - Tworzenie szablonu pliku stały aparatu Unity.

## <a name="1602"></a>1.6.0.2

Wydana 24 lipca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

  - Wycofane obejście dla aparatu Unity usterka wydajności, który został rozwiązany przez aparat Unity.

## <a name="1601"></a>1.6.0.1

Wydana 10 lipca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

  - Obsługuje stały barwy kodu programu do cieniowania.

## <a name="1600"></a>1.6.0.0

Wydana 26 czerwca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Kreatorów:**

  - Naprawiono błąd pisowni OnApplicationFocus komunikat.

- **Generowanie projektu:**

  - Obejście przejściowych błędów wydajności aparatu Unity: pamięci podręcznej MonoIslands podczas generowania projektów.

  - Nie można konwertować przenośnego pliku pdb mdb już korzystając z nowego środowiska uruchomieniowego platformy Unity.

## <a name="1502"></a>1.5.0.2

Wydana 18 kwietnia 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Dodano obsługę podstawowych uzupełnianie kodu programu do cieniowania.

  - Dodano obsługę przełączanie komentarze w plikach programu do cieniowania.

## <a name="1501"></a>1.5.0.1

Wydana 28 marca 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Dodano obsługę dodatkowych szablonów w Eksploratorze projektów aparatu Unity.

## <a name="1500"></a>1.5.0.0

Wydana 21 marca 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Dodano obsługę wykrywania i dołączanie do graczy systemu Android połączone za pośrednictwem portu USB.

## <a name="1403"></a>1.4.0.3

Wydanie 5 marca 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę nowych generator projektu w 2018.1 aparatu Unity.

- **Integracja:**

  - Dodano opcję panel ustawień dedykowanego.

## <a name="1402"></a>1.4.0.2

Wydana 24 stycznia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Wykrywanie poprawionej wersji platformy Mono.

- **Integracja:**

  - Rozwiązano problemy dotyczące synchronizacji z 2018.1 i aktywacją wtyczka.

  - Naprawiono powiadomienia, gdy nowy gracz wykrywanie.

## <a name="1401"></a>1.4.0.1

Wydana 23 stycznia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

  - Kliknij dwukrotnie stały folderów Rozwiń/Zwiń na

## <a name="1400"></a>1.4.0.0

Wydana 13 grudnia 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę dla platformy .NET Standard.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

  - Stałym pdb automatyczne do konwersji symboli debugowania mdb.

## <a name="1301"></a>1.3.0.1

Wydana 12 grudnia 2017 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

  - Naprawiono wywołanie pośrednie EditorPrefs.GetBool wpływające na panelu Inspektor podczas próby zmiany rozmiaru tablicy.

- **Kreatorów:**

  - Odśwież kontekstu roslyn przed wstawieniem metody.

## <a name="1300"></a>1.3.0.0

Wydana 20 listopada 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Kreatorów:**

  - Dodano Kreator "Unity zaimplementuj komunikat".

  - Dodano obsługę nowych zakończenia interfejsu API w programie VS dla komputerów Mac w wersji 7.4.

## <a name="1200"></a>1.2.0.0

Wydana 23 października 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Dodano obsługę plików symboli debugowania przenośnej.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono rozszerzenie .dll dodatkowe błędnie dodane do nazwy pliku zestawu.

  - Nie Wymuszaj flagi AllowAttachedDebuggingOfEditor Unity, zgodnie z wartością domyślną jest teraz "true".

## <a name="1103"></a>1.1.0.3

Wydana 23 października 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę profilu .NET 4.6.

## <a name="1102"></a>1.1.0.2

Wydana 8 sierpnia 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Rozpocznij dialogowym Dołącz do procesu, jeśli nie masz pewności która Unity można dołączyć do.

- **Generowanie projektu:**

  - Zawsze należy włączyć niebezpieczne kompilacji przełącznika, gdy jest używane środowisko Unity 5.6.

## <a name="1101"></a>1.1.0.1

Wydana 20 lipca 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Dodano obsługę zlokalizowanych zasobów.

## <a name="1100"></a>1.1.0.0

Wydana 12 lipca 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

  - Dodano obsługę dołączania do graczy i edytory za pośrednictwem Dołącz do procesu okna.

- **Generowanie projektu:**

  - Naprawiono zestawu odwołania do nazwy mcs.rsp plików.

  - Dodano obsługę jednostki kompilacji assembly.json.

  - Naprawiono definiuje ze poziomy interfejsu API.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

  - Komunikat o błędzie cieniowania stałych podczas kompilowania kodu.

## <a name="1001"></a>1.0.0.1

Wydana 4 maja 2017 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

  - Naprawiono aktywne śledzenie dokumentów oraz hybrydowych i standardowych projektów.

## <a name="1000"></a>1.0.0.0

Wydana 3 maja 2017 r.
