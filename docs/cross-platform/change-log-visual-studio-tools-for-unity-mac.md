---
title: Zmienianie dziennika (Visual Studio Tools for Unity, komputery Mac) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 78ef5d4961f76f654a6d3b1aa7b0089f21a44aa5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107843"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Dziennik zmian (narzędzia Visual Studio Tools for Unity, komputery Mac)
Dziennik zmian w programie Visual Studio Tools for Unity.

## <a name="2020"></a>2.0.2.0
 wydana 2 kwietnia 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

    - Dodano obsługę automatycznego odświeżania bazy danych zasobów firmy Unity na zapisanie. To jest domyślnie włączona i wyzwoli ponowną kompilację po stronie platformy Unity podczas zapisywania skryptu w programie Visual Studio. Można wyłączyć tę funkcję w Tools\Options\Tools, aby zapisać AssetDatabase Unity\Refresh Unity na.

    - Dodano obsługę ustawiania instalacji preferowanego środowiska unity dokumentację w trybie offline.

    - Menu kontekstowe dodanych funkcji nowego edytora.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

    - Naprawiono zestawu inspekcji filtrowania i ramki za pomocą klatek puste.

## <a name="2011"></a>2.0.1.1
 wydana 26 marca 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

    - Tymczasowo wprowadzić Mono domyślne, a tylko można używać debugera dla tej wersji bardzo szczegółowych.

## <a name="2006"></a>2.0.0.6
 wydana 26 marca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

    - Dodano obsługę "Dołącz do aparatu Unity i Odtwórz".

## <a name="2005"></a>2.0.0.5
 wydana 20 marca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

    - Zachowaj właściwości zewnętrznych podczas przetwarzania pliku rozwiązania.

## <a name="2004"></a>2.0.0.4
 wydana 5 marca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

    - Zaktualizowano ScriptableObject interfejsu API.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

    - Usunięto przestrzeni nazw za pomocą szablonów.

## <a name="2003"></a>2.0.0.3
 wydana 5 marca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

    - Pola publiczne i serializacji nie jest już spowoduje ostrzeżenia. Firma Microsoft została automatycznie pominąć ostrzeżenia kompilatora CS0649 i IDE0051 w projektów aparatu Unity, utworzone te komunikaty.

- **Integracja:**

    - Monit, aby dołączyć do konkretne wystąpienie, jeśli działa więcej ten jeden proces aparatu Unity.

- **Ocena:**

    - Dodano obsługę funkcji lokalnych.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

    - Naprawiono odczytywanie atrybutem niestandardowym argumentów nazwanych, używając starej wersji protokołu.

## <a name="2002"></a>2.0.0.2
 wydana 4 lutego 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracja:**

    - Zaktualizowano obiekt MonoBehaviour interfejsu API.
   
### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

    - Naprawiono ustawiania pierwotnych wartości w debugerze.

## <a name="2001"></a>2.0.0.1
 wydanie: 4 grudnia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja:**

    - Naprawiono zawierania własny pakiet instalacji.

## <a name="2000"></a>2.0.0.0
 wydanie: 4 grudnia 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

    - Zastąpione debugerze Unity na komputerze Mac ten sam debuger aparatu Unity core z Windows.

    - Zastąpione NRefactory na rzecz Roslyn do obliczenia wyrażenia.

    - Dodano obsługę dla wskaźników: wyłuskanie rzutowania i arytmetyka wskaźnika (Unity 2018.2 + i nowego środowiska uruchomieniowego są wymagana dla tego).

    - Dodano obsługę widoku wskaźnika tablicy (na przykład w języku C++). Wykonaj wyrażenie wskaźnika, a następnie dołącz przecinek i liczbę elementów, które mają być wyświetlane.

    - Dodano obsługę konstrukcji asynchronicznej.

    - Dodano obsługę zmienne pseudo (identyfikatorów wyjątków i obiektu).
    
### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

    - Obliczanie wyrażenia stałej z wyrażeniami źle sformułowane lub nieobsługiwany.

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
