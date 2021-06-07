---
title: Dziennik zmian (Visual Studio Tools for Unity, Komputery Mac) | Microsoft Docs
description: Wyświetl dziennik zmian dla komputerów Visual Studio Tools for Unity Mac. Zobacz zmiany z wersji 1.0.0.0 do 2.7.0.0 lub nowszą.
ms.custom: ''
ms.date: 6/3/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 2d3faf8e5231ca5d2e99bcf80dc18b6d4f4607cd
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448301"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Dziennik zmian (narzędzia Visual Studio Tools for Unity, komputery Mac)

Visual Studio Tools for Unity dziennika zmian.

## <a name="21020"></a>2.10.2.0
Wydany 2 czerwca 2021 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md) diagnostykę. Nadaj obliczeniem skalarnych priorytet nad obliczeniami wektorów.

- **Oceny:**

  - Dodano obsługę używania przenośnych symboli pdb w celu poprawnego filtrowania widocznych lokalizacji lokalnych.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Poprawiono ogłaszanie analizowania przez odtwarzacz w najnowszych wersjach aparatu Unity.

## <a name="21010"></a>2.10.1.0
Wydany 11 maja 2021 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązano problemy ze stabilnością przy [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md) użyciu szybkiej poprawki.

  - Rozwiązano problemy z wydajnością wątków.

  - Naprawiono filtrowanie pominiętych ostrzeżeń i błędów na liście błędów.

  - Naprawiono filtrowanie procesów w tle aparatu Unity.

## <a name="21000"></a>2.10.0.0
Wydany 13 kwietnia 2021 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano [`UNT0019`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0019.md) diagnostykę. Niepotrzebne wywołanie pośrednie dla `GameObject.gameObject` .

  - Dodano [`UNT0020`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0020.md) diagnostykę. `MenuItem` atrybut używany w metodzie niestatycznej.

  - Dodano [`UNT0021`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0021.md) diagnostykę. Komunikat aparatu Unity powinien być chroniony (opcjonalnie).

  - Dodano [`UNT0022`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0022.md) diagnostykę. Nieefektywna metoda ustawienia pozycji i obrotu.

  - Dodano [`UNT0023`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0023.md) diagnostykę. Coalescing assignment on Unity objects (Przypisywanie do obiektów Unity).

  - Dodano [`USP0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0017.md) suppressor dla `IDE0074` . Obiekty aparatu Unity nie powinny używać przypisania coalescing.

## <a name="2940"></a>2.9.4.0
Wydany 6 kwietnia 2021 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązywanie problemów z wyliczaniem testów

## <a name="2930"></a>2.9.3.0
Wydany 30 marca 2021 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązywanie problemów z testowym runnerem 

## <a name="2920"></a>2.9.2.0
Wydana 2 marca 2021 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono wyróżnianie wyszukiwania w oknie dialogowym komunikatu aparatu Unity.

  - Rozwiązano problemy ze stabilnością w widoku drzewa projektu aparatu Unity.

- **Debugowania:**

  - Naprawiono obsługę warunkowych punktów przerwania.

## <a name="2910"></a>2.9.1.0
Wydany 9 lutego 2021 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę uruchamiania i debugowania testów aparatu Unity ze środowiska IDE

- **Oceny:**

  - Dodano `Active Scene` do lokalizacji lokalnych z obiektami gry głównej.

  - Dodane `this.gameObject` do lokalizacji lokalnych, biorąc pod uwagę, że jest szeroko używane w projektach aparatu Unity.

  - Dodano grupy i do wszystkich wystąpień, aby można było łatwo wyświetlić `Children` `Components` całą `GameObject` hierarchię obiektów.

  - Dodano `Scene Path` do `GameObject` wszystkich wystąpień, aby pokazać lokalizację w scenie.

  - Dodano obsługę `JobEntityBatch` /Lambdas w przypadku używania jednostek z generatorami źródłowymi.

  - Ulepszono obsługę wyświetlania dużych tablic (przy użyciu zasobników indeksów).

  - Dodano brakujące komunikaty aparatu Unity dla interfejsu API 2019.4.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązano problemy ze stabilnością w oknie dialogowym komunikatu aparatu Unity

  - Rozwiązano różne problemy z interfejsem użytkownika w językach innych niż ENU.

  - Rozwiązano problemy ze stabilnością w [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) diagnostyce.

- **Debugowania:**

  - Rozwiązano problemy z rozłączaniem maszyny wirtualnej podczas korzystania z `Trace` metod.

- **Oceny:**

  - Naprawiono filtrowanie przestarzałych właściwości, które zgłaszały wyjątki.

## <a name="2900"></a>2.9.0.0
Wydany 20 stycznia 2021 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę `raytrace shaders` plików `UXML` i `USS` .

  - Zaktualizowano interfejs API komunikatów aparatu Unity (dla wszystkich metod używanych jako coroutines).

  - Zaktualizowano Android SDK wykrywania.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) diagnostykę, dając nieprawidłowe ostrzeżenia dla coroutines i `AssetPostprocessor.OnAssignMaterialModel` .

## <a name="2840"></a>2.8.4.0
Wydany 15 grudnia 2020 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązano problem z niezawodnością podczas zamykania kreatora tworzenia zdarzeń aparatu Unity.

## <a name="2830"></a>2.8.3.0
Wydany 10 listopada 2020 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono dołączanie do aparatu Unity, nawet jeśli w rozwiązaniu nie ma projektu VSTU.

## <a name="2820"></a>2.8.2.0
Wydany 27 października 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Ulepszono [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md) diagnostykę w celu zastosowania do wszystkiego, co dziedziczy z `Component` , a nie tylko `MonoBehaviour` .

## <a name="2810"></a>2.8.1.0
Wydany 13 października 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Oceny:**

  - Dodano obsługę niejawnej konwersji za pomocą wywołania. Wcześniej ewaluator wymuszał ścisłe sprawdzanie typów, co było wynikiem `Failed to find a match for method([parameters...])` komunikatów ostrzegawczych.

- **Integracji:**

  - Dodano [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) diagnostykę. Nie należy używać funkcji w komunikatach o `System.Reflection` krytycznym znaczeniu dla `Update` wydajności, takich `FixedUpdate` jak , , `LateUpdate` lub `OnGUI` .

  - Ulepszone [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) i [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) pomijacze z obsługą wszystkich `AssetPostprocessor` metod statycznych.

  - Dodano [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md) suppressor dla `CS8618` . `C# 8.0` wprowadzono typy referencyjne dopuszczace wartość null i typy referencyjne, które nie mogą dopuszczać wartości null. Wykrywanie inicjalizacji typów dziedziczonych z `UnityEngine.Object` nie jest obsługiwane i spowoduje błędy.

  - Teraz korzystasz z tego samego odtwarzacza i mechanizmu generowania projektu asmdef dla aparatu Unity 2019.x i 2020.x+.
  
  - Ulepszone środowisko użytkownika podczas generowania komunikatów aparatu Unity za pomocą kreatora.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono nieoczekiwane uzupełnianie komunikatów w komentarzach.

## <a name="2800"></a>2.8.0.0 
Wydany 14 września 2020 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono generowanie projektu odtwarzacza za pomocą aparatu Unity 2019.x.

## <a name="2710"></a>2.7.1.0
Wydana 5 sierpnia 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Zaktualizowano interfejs API komunikatów aparatu Unity do wersji 2019.4.

  - Dodano [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) suppressor dla `CA1823` . Pola prywatne z atrybutami lub nie `SerializeField` powinny być oznaczone jako `SerializeReference` nieużywane (FxCop).
  
  - Dodano [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) suppressor dla `CA1822` . Komunikaty aparatu Unity nie powinny być oflagowane jako kandydaci `static` do modyfikatora (FxCop).

  - Dodano [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) suppressor dla `CA1801` . Nieużywanych parametrów nie należy usuwać z komunikatów aparatu Unity (FxCop).
  
  - Dodano `MenuItem` obsługę do [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) pomijania.  

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) metody i pomijały, które nie działają z [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) dodatkowymi nawiasami ani z argumentami metody.
  
  - Naprawiono obowiązkowe odświeżanie bazy danych zasobów nawet wtedy, gdy automatyczne odświeżanie zostało wyłączone w ustawieniach aparatu Unity.

## <a name="2700"></a>2.7.0.0
Wydany 23 czerwca 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę utrwalania folderów rozwiązań, gdy unity ponownie generuje rozwiązanie i projekty.

  - Dodano [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) diagnostykę. Wykryj niepoprawny podpis metody za `InitializeOnLoadMethod` pomocą atrybutu `RuntimeInitializeOnLoadMethod` lub .

  - Dodano [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) diagnostykę. Użycie `Invoke` wartości , lub z pierwszym `InvokeRepeating` `StartCoroutine` `StopCoroutine` argumentem jako literału ciągu nie jest bezpieczne.

  - Dodano [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) diagnostykę. `SetPixels` wywołania jest powolne.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono tworzenie punktów przerwania, gdy gra była uruchamiana na starej środowisko uruchomieniowe Mono (próba powiązania punktu przerwania zaraz po jego utworzeniu). 
  
- **Integracji:**

  - Nie resetuj zaznaczenia podczas filtrowania komunikatów w kreatorze komunikatów aparatu Unity.
  
  - Naprawiono elementy , i z następującymi regułami: pomijaj (tylko do odczytu), (nieużywane), (nigdy nie przypisano) dla wszystkich pól dekorowanych [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) `IDE0044` `IDE0051` `CS0649` atrybutem SerializeField. Pomijaj element `CS0649` (nigdy nieprzypisane) dla pól publicznych wszystkich typów rozszerzających elementy `Unity.Object`.

  - Naprawiono sprawdzanie parametrów typu ogólnego dla [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) .

- **Oceny:**

  - Naprawiono porównywanie równości z wylikami.

## <a name="2610"></a>2.6.1.0
Wydany 19 maja 2020 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Ostrzegaj, jeśli nie możemy utworzyć serwera obsługi komunikatów po stronie aparatu Unity.

  - Prawidłowo uruchamiaj analizatory podczas uproszczonej kompilacji.

  - Poprawiono dokumentację interfejsu API z instalacjami usługi Unity Hub.
  
  - Rozwiązano problem z awarią wizualizatora debugera.

## <a name="2600"></a>2.6.0.0
Wydany 14 kwietnia 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) diagnostykę. Wykrywanie i zawijanie wywołań do coroutines w `StartCoroutine()` .

  - Dodano [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) diagnostykę. Wykrywanie i usuwanie nieprawidłowego lub nadmiarowego `SerializeField` atrybutu.

  - Dodano [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) diagnostykę. Wykryj `GetComponent()` wywołaną z typem niebędącym składnikiem lub typem bez interfejsu.

  - Dodano [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) suppressor dla `IDE0051` . Nie flaguj metod z `ContextMenu` atrybutem lub przywołynych przez pole z `ContextMenuItem` atrybutem jako nieużywane.

  - Dodano [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) suppressor dla `IDE0051` . Nie flaguj pól z `ContextMenuItem` atrybutem jako nieużywane.

  - Dodano [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) suppressor dla `IDE0044` . Nie należy pól z `ContextMenuItem` atrybutem tylko do odczytu.

  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md)Wartości [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) i działają teraz dla atrybutów i [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) `SerializeReference` `SerializeField` .

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Polecenia uruchamiania/zatrzymania wysyłaj do aparatu Unity tylko wtedy, gdy edytor jest w stanie się komunikować.

  - Poprawiono dokumentację szybkich informacji z komunikatami dziedziczoną.

  - Naprawiono zakres `CreateInspectorGUI` komunikatów dla wiadomości.

  - Nie zgłaszaj [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) metod za pomocą modyfikatorów polimorficznych.

- **Oceny:**

  - Naprawiono obsługę aliasowanych using.
  
  - Naprawiono obsługę wartości null.  

## <a name="2520"></a>2.5.2.0

Wydana 23 marca 2020 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono rejestrację wątków po dołączeniu.

## <a name="2510"></a>2.5.1.0

Wydana 3 marca 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) suppressor dla `IDE0051` . Metody prywatne używane z metodami Invoke, InvokeRepeating, StartCoroutine lub StopCoroutine nie powinny być oznaczane jako nieużywane.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono dokumentację OnDrawGizmos/OnDrawGizmosSelected.

- **Oceny:**

  - Naprawiono inspekcję argumentów lambda.

## <a name="2501"></a>2.5.0.1

Wydany 19 lutego 2020 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) sprawdzanie diagnostyczne pod celu sprawdzenia, czy podpis komunikatu jest nieprawidłowy. Podczas inspekcji typów z wieloma poziomami dziedziczenia ta diagnostyka może się nie powieść z następującym komunikatem: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="2500"></a>2.5.0.0

Wydany 22 stycznia 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę plików HLSL.
  
  - Przełączony na interfejs użytkownika okna dialogowego nowego folderu.
  
  - Przełączony na nową siatkę właściwości z ułatwieniami dostępu dla ustawień.

  - Dodano [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) suppressor dla `IDE0051` . Pola prywatne z `SerializeField` atrybutem nie powinny być oznaczone jako nieużywane.

  - Dodano [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) suppressor dla `CS0649` . Pola z `SerializeField` atrybutem nie powinny być oznaczone jako nieprzypisane.  

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono generowanie projektu `GenerateTargetFrameworkMonikerAttribute` (element docelowy nie zawsze był poprawnie zlokalizowany).

- **Oceny:**

  - Naprawiono ocenę ciągów (nie używając wywołań ToString()

## <a name="2420"></a>2.4.2.0

Wydany 3 grudnia 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono diagnostykę za pomocą interfejsów zdefiniowanych przez użytkownika.

  - Naprawiono szybkie etykietki narzędzi z źle sformułowanych wyrażeniami.
  
## <a name="2410"></a>2.4.1.0

Wydany 6 listopada 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę procesów w tle aparatu Unity. (Debuger może automatycznie łączyć się z głównym procesem zamiast procesem podrzędnym).

  - Dodano szybką etykietkę narzędzia dla komunikatów aparatu Unity z wyświetloną skojarzoną dokumentacją.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono analizator porównania tagów `UNT0002` z zaawansowanymi wyrażeniami binarnymi i wyrażeniami wywołania.

### <a name="deprecated-features"></a>Przestarzałe funkcje

- **Integracji:**

  - W przyszłości Visual Studio Tools for Unity będą obsługiwać tylko Visual Studio 2017+.

## <a name="2400"></a>2.4.0.0

Wydany 15 października 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) pomijanie `IDE0060` dla (nieużywanego parametru) dla wszystkich komunikatów aparatu Unity.

  - Dodano szybką etykietkę narzędzia dla pól oznaczonych tagiem `TooltipAttribute` . (Będzie to również działać w przypadku prostego uzyskiwania dostępu przy użyciu tego pola).

## <a name="2330"></a>2.3.3.0

Wydany 23 września 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano nowy suppressor dla środowiska IDE0060, aby uniemożliwić ideom wyświetlanie szybkiej poprawki w celu usunięcia nieużywanych parametrów.
    - `USP0005` for `IDE0060` : komunikaty aparatu Unity są wywoływane przez środowisko uruchomieniowe aparatu Unity.

## <a name="2320"></a>2.3.2.0

Wydany 16 września 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Pogłębiliśmy wiedzę o tym, że Visual Studio dla projektów Unity, dodając nową diagnostykę specyficzną dla aparatu Unity. Wprowadziliśmy również zmiany powodujące, że środowisko IDE działa teraz bardziej inteligentnie dzięki pomijaniu ogólnej diagnostyki języka C#, która nie dotyczy projektów Unity. Na przykład w idee nie będzie pokazywana szybka poprawka zmiany zmiennej inspektora, co uniemożliwi zmodyfikowanie zmiennej w `readonly` edytorze aparatu Unity.
    - `UNT0001`: komunikaty aparatu Unity są wywoływane przez środowisko uruchomieniowe, nawet jeśli są puste, nie deklaruj ich, aby uniknąć nieskomplikowania przetwarzania przez środowisko uruchomieniowe aparatu Unity.
    - `UNT0002`: Porównanie tagów przy użyciu równości ciągów jest wolniejsze niż wbudowana metoda CompareTag.
    - `UNT0003`: Użycie ogólnej formy GetComponent jest preferowane ze względu na bezpieczeństwo typów.
    - `UNT0004`: Komunikat aktualizacji jest zależny od szybkości ramki i powinien używać wartości Time.deltaTime zamiast Time.fixedDeltaTime.
    - `UNT0005`: komunikat FixedUpdate jest niezależny od szybkości ramki i powinien używać wartości Time.fixedDeltaTime zamiast Time.deltaTime.
    - `UNT0006`: wykryto niepoprawną sygnaturę metody dla tego komunikatu aparatu Unity.
    - `UNT0007`: Unity zastępuje operator porównania wartości null dla obiektów Unity, które są niezgodne z ujednamianie wartości null.
    - `UNT0008`: Unity zastępuje operator porównania wartości null dla obiektów Unity, które są niezgodne z propagacja wartości null.
    - `UNT0009`: Podczas stosowania atrybutu InitializeOnLoad do klasy należy podać konstruktor statyczny. Atrybut InitializeOnLoad zapewnia, że zostanie on wywołany podczas uruchamiania edytora.
    - `UNT0010`: Składniki MonoBehaviour powinny być tworzone tylko przy użyciu funkcji AddComponent(). MonoBehaviour to składnik, który musi zostać dołączony do obiektu GameObject.
    - `UNT0011`: ScriptableObject należy tworzyć tylko przy użyciu funkcji CreateInstance(). Obiekt ScriptableObject musi zostać utworzony przez aparat Unity do obsługi metod komunikatów aparatu Unity.
    - `USP0001` for `IDE0029` : Obiekty aparatu Unity nie powinny używać funkcji coalescing o wartości null.
    - `USP0002` for `IDE0031` : Obiekty aparatu Unity nie powinny używać propagacji wartości null.
    - `USP0003` for `IDE0051` : komunikaty aparatu Unity są wywoływane przez środowisko uruchomieniowe aparatu Unity.
    - `USP0004` dla `IDE0044` : Pola z atrybutem SerializeField nie powinny być tylko do odczytu.

## <a name="2310"></a>2.3.1.0

Wydany 4 września 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Oceny:**

  - Dodano obsługę lepszego wyświetlania typów, tj. `List<object>` zamiast `List'1[[System.Object, <corlib...>]]` .

  - Dodano obsługę dostępu do wskaźnika członkowskiego, `p->data->member` tj. .

  - Dodano obsługę niejawnych konwersji w inicjatorach tablic, `new byte [] {1,2,3,4}` tj. .

  - Dodano obsługę edytora hex podczas inspekcji tablic bajtów i ciągów.

## <a name="2300"></a>2.3.0.0

Wydany 13 sierpnia 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oceny:**

  - Rozwiązano problemy z wykonywaniem krok po kroku z wyjątkami.

  - Naprawiono ocenę identyfikatorów pseudo (takich jak $exception).

  - Zapobiegaj awarii podczas wyłuskania nieprawidłowych adresów.  

  - Rozwiązano problem z niezaładowanych domen aplikacji.

## <a name="2200"></a>2.2.0.0

Wydany 25 lipca 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oceny:**

  - Naprawiono inspekcję za pomocą typów IntPtr.

- **Debuger:**

  - Naprawiono obsługę punktów kontrolnych i punktów przerwania funkcji.

## <a name="2130"></a>2.1.3.0

Wydany 9 lipca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Dodano obsługę przechwytowania podklas wyjątków.

  - Dodano obsługę protokołu MDS 2.51.

- **Integracji:**

  - Dodano obsługę plików asmdef.

  - Przełącz się do trybu zmiany nazwy po dodaniu pliku z szablonu (aby naśladować zachowanie edytora aparatu Unity).

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono obsługę źle sformułowanych komunikatów podczas komunikacji z odtwarzaczami Unity.

- **Oceny:**

  - Naprawiono obsługę przestrzeni nazw w wyrażeniach.

## <a name="2120"></a>2.1.2.0

Wydany 2 lipca 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oceny:**

  - Naprawiono raportowanie błędów z wyrażeniami, których nie można analizowania.

## <a name="2110"></a>2.1.1.0

Wydany 27 czerwca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Zaktualizowano interfejs API MonoBehaviour do wersji 2019.1.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Poprawiono wydajność eksploratora projektów aparatu Unity.

  - Naprawiono ostrzeżenia i błędy raportowania w danych wyjściowych po włączeniu uproszczonej kompilacji.

  - Poprawiono uproszczone działanie kompilacji.

## <a name="2100"></a>2.1.0.0

Wydany 20 czerwca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Wyłączono pełną kompilację dla projektów Unity na rzecz używania błędów i ostrzeżeń funkcji IntelliSense. W rzeczywistości unity tworzy Visual Studio z projektami biblioteki klas, które reprezentują to, co unity robi wewnętrznie. Oznacza to, że wynik kompilacji w programie Visual Studio nigdy nie jest używany ani odbierany przez unity, ponieważ ich potok kompilacji jest zamknięty. Tworzenie w Visual Studio po prostu zużywa zasoby bez żadnych zasobów. Jeśli potrzebujesz pełnej kompilacji, ponieważ masz narzędzia lub konfigurację, która od niego zależy, możesz wyłączyć tę optymalizację (Ustawienia/Narzędzia dla aparatu Unity/Wyłącz pełną kompilację projektów).
  
  - Dodano obsługę pakietów aparatu Unity w upe. Widoczne są tylko pakiety, do których istnieją odwołania (manifest.jsw folderze ) i Pakiety `Packages` lokalne (osadzone w `Packages` folderze ).

## <a name="2021"></a>2.0.2.1

Wydany 30 maja 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano ikonę niestandardową dla celów wykonywania aparatu Unity.

## <a name="2020"></a>2.0.2.0

Wydany 2 kwietnia 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę automatycznego odświeżania bazy danych zasobów aparatu Unity podczas zapisywania. Ta funkcja jest domyślnie włączona i spowoduje wyzwolenie ponownej kompilacji po stronie aparatu Unity podczas zapisywania skryptu w Visual Studio. Możesz wyłączyć tę funkcję w menu Tools\Options\Tools for Unity\Refresh Unity's AssetDatabase on save (Narzędzia\Opcje\Narzędzia dla aparatu Unity\Odśwież bazę danych AssetDatabase aparatu Unity przy zapisywaniu).

  - Dodano obsługę ustawiania preferowanej instalacji aparatu Unity dla dokumentacji w trybie offline.

  - Dodano menu kontekstowe dla nowego edytora.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono filtrowanie zestawu i inspekcję ramek z pustymi ramkami.

## <a name="2011"></a>2.0.1.1
 
 Wydany 26 marca 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Tymczasowo spraw, aby mono było domyślnym i tylko użytecznym debugerem dla tej bardzo określonej wersji.

## <a name="2006"></a>2.0.0.6

Wydany 26 marca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę dołączania do aparatu Unity i odtwarzania.

## <a name="2005"></a>2.0.0.5

Wydany 20 marca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Zachowaj właściwości zewnętrzne podczas przetwarzania pliku rozwiązania.
  
- **Oceny:**

  - Dodano obsługę nazw kwalifikowanych za aliasem (na razie tylko globalnej przestrzeni nazw). Dlatego ewaluator wyrażeń akceptuje teraz typy przy użyciu formularza global::namespace.type.

  - Dodano obsługę `pointer[index]` formularza, który jest semantycznie identyczny z formularzem wyłuskania `*(pointer+index)` wskaźnika.

## <a name="2004"></a>2.0.0.4

Wydany 5 marca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Zaktualizowano `ScriptableObject` interfejs API.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Usunięto przestrzenie nazw z szablonów.

## <a name="2003"></a>2.0.0.3
 
 Wydany 5 marca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Pola publiczne i serializowane nie będą już powodować ostrzeżeń. Automatycznie pominięto ostrzeżenia kompilatora i w projektach `CS0649` `IDE0051` aparatu Unity, które utworzyły te komunikaty.

- **Integracji:**

  - Monituj o dołączenie do określonego wystąpienia, jeśli jest uruchomiony więcej niż jeden proces aparatu Unity.

- **Oceny:**

  - Dodano obsługę funkcji lokalnych.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono odczytywanie atrybutu niestandardowego dla nazwanych argumentów w przypadku używania starych wersji protokołu.

## <a name="2002"></a>2.0.0.2

Wydany 4 lutego 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Zaktualizowano interfejs API MonoBehaviour.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono ustawianie wartości pierwotnych w debugerze.

## <a name="2001"></a>2.0.0.1

Wydany 4 grudnia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązano problem z samodzielnym pakietem instalacyjnym.

## <a name="2000"></a>2.0.0.0
 Wydany 4 grudnia 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Zastąpiono debuger aparatu Unity na komputerze Mac tym samym debugerem podstawowym aparatu Unity z systemu Windows.

  - Zastąpiono NRefactory na rzecz programu Roslyn w celu oceny wyrażeń.

  - Dodano obsługę wskaźników: wyłuskanie, rzutowanie i arytmetyka wskaźnika (w tym celu wymagane jest środowisko Unity 2018.2+ i nowe środowisko uruchomieniowe).

  - Dodano obsługę widoku wskaźnika tablicy (na przykład w języku C++). Weź wyrażenie wskaźnika, a następnie dołącz przecinek i liczbę elementów, które chcesz zobaczyć.

  - Dodano obsługę konstrukcji asynchronicznych.

  - Dodano obsługę zmiennych pseudo (identyfikatorów wyjątków i obiektów).

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono ocenę wyrażeń za pomocą źle sformułowanych lub nieobsługiwanych wyrażeń.

## <a name="1700"></a>1.7.0.0

Wydany 13 listopada 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Dodano więcej informacji o kliencie (adres IP, nazwa komputera) w oknie dialogowym dołączania.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono zakleszczenie w bibliotece używane do komunikowania się z aparatem debugera aparatu Unity, co powoduje zablokowanie aparatu Visual Studio lub Unity, szczególnie w przypadku trafienia przycisku "Dołącz do aparatu Unity" lub ponownego uruchomienia gry.

- **Integracji:**

  - Naprawiono aktywację wtyczki aparatu Unity po wybraniu innego edytora domyślnego.

  - Naprawiono tworzenie szablonu pliku aparatu Unity.

## <a name="1602"></a>1.6.0.2

Wydany 24 lipca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Wycofano obejście błędu wydajności aparatu Unity, który został naprawiony przez unity.

## <a name="1601"></a>1.6.0.1

Wydany 10 lipca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono obsługę kolorowania kodu cieniowania.

## <a name="1600"></a>1.6.0.0

Wydany 26 czerwca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Kreatorów:**

  - Poprawiono literówkę z komunikatem OnApplicationFocus.

- **Generowanie projektu:**

  - Przejściowe obejście błędu wydajności aparatu Unity: buforowanie rozwiązania MonoIslands podczas generowania projektów.

  - Nie należy już konwertować przenośnego pliku pdb na mdb podczas korzystania z nowego środowiska uruchomieniowego aparatu Unity.

## <a name="1502"></a>1.5.0.2

Wydany 18 kwietnia 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę podstawowego uzupełniania kodu cieniowania.

  - Dodano obsługę przełączanie komentarzy w plikach cieniowania.

## <a name="1501"></a>1.5.0.1

Wydana 28 marca 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę dodatkowych szablonów w eksploratorze projektów aparatu Unity.

## <a name="1500"></a>1.5.0.0

Wydana 21 marca 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę wykrywania i dołączania do odtwarzaczy systemu Android połączonych za pośrednictwem portu USB.

## <a name="1403"></a>1.4.0.3

Wydana 5 marca 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę nowego generatora projektu w a aparatu Unity 2018.1.

- **Integracji:**

  - Dodano panel opcji dla ustawień dedykowanych.

## <a name="1402"></a>1.4.0.2

Wydany 24 stycznia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono wykrywanie wersji mono.

- **Integracji:**

  - Rozwiązano problemy z chronometrażu w 2018.1 i aktywacji wtyczki.

  - Naprawiono powiadomienia podczas wykrywania nowego odtwarzacza.

## <a name="1401"></a>1.4.0.1

Wydana 23 stycznia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono foldery rozwijania/zwijania po dwukrotnym kliknięciu

## <a name="1400"></a>1.4.0.0

Wydany 13 grudnia 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę .NET Standard.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono automatyczną konwersję symboli debugowania pdb do mdb.

## <a name="1301"></a>1.3.0.1

Wydany 12 grudnia 2017 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono pośrednie wywołanie funkcji EditorPrefs.GetBool wpływające na inspektora podczas próby zmiany rozmiaru tablicy.

- **Kreatorów:**

  - Odśwież kontekst roslyn przed wstawianiem metody.

## <a name="1300"></a>1.3.0.0

Wydana 20 listopada 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Kreatorów:**

  - Dodano kreatora "Implementowanie komunikatu aparatu Unity".

  - Dodano obsługę nowego interfejsu API uzupełniania w programie VS dla komputerów Mac w wersji 7.4.

## <a name="1200"></a>1.2.0.0

Wydana 23 października 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Dodano obsługę przenośnych plików symboli debugowania.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono dodatkowe .dll błędnie dodane do nazwy pliku zestawu.

  - Nie wymuszaj flagi AllowAttachedDebuggingOfEditor Unity, ponieważ wartość domyślna to teraz "true".

## <a name="1103"></a>1.1.0.3

Wydana 23 października 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę profilu .NET 4.6.

## <a name="1102"></a>1.1.0.2

Wydana 8 sierpnia 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Jeśli nie masz pewności, do którego aparatu Unity chcesz dołączyć, uruchom okno dialogowe dołączania do procesu.

- **Generowanie projektu:**

  - Zawsze włączaj niebezpieczny przełącznik kompilacji, gdy jest używane unity 5.6.

## <a name="1101"></a>1.1.0.1

Wydany 20 lipca 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę zlokalizowanych zasobów.

## <a name="1100"></a>1.1.0.0

Wydana 12 lipca 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę dołączania do odtwarzaczy i edytorów za pośrednictwem okna Dołączanie do procesu.

- **Generowanie projektu:**

  - Naprawiono odwołania do nazw zestawu w plikach mcs.rsp.

  - Dodano obsługę assembly.jsw jednostkach kompilacji.

  - Naprawiono definicje z poziomami interfejsu API.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono komunikat o błędzie cieniowania podczas kompilowania.

## <a name="1001"></a>1.0.0.1

Wydana 4 maja 2017 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono śledzenie aktywnych dokumentów w projektach hybrydowych i zwykłych.

## <a name="1000"></a>1.0.0.0

Wydana 3 maja 2017 r.
