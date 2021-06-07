---
title: Dziennik zmian (Visual Studio Tools for Unity, Windows) | Microsoft Docs
description: Wyświetl dziennik zmian dla systemu Visual Studio Tools for Unity Windows. Zobacz zmiany z wersji od 1.0.0.0 do 4.7.0.0 lub nowszą.
ms.custom: ''
ms.date: 6/2/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 2ff13b017ffe0d310ddfd1b302c6436e9d708a36
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448314"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Dziennik zmian (Visual Studio Tools for Unity, Windows)

Visual Studio Tools for Unity dziennika zmian.

## <a name="41020"></a>4.10.2.0
Wydany 25 maja 2021 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md) diagnostykę. Nadaj obliczeń skalarnych priorytet nad obliczeniami wektorów.

- **Oceny:**

  - Dodano obsługę używania przenośnych symboli pdb w celu poprawnego filtrowania widocznych lokalizacji lokalnych.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Stabilność wyszukiwania odwoływnych zasobów stałych.

  - Naprawiono ogłaszanie analizy przez odtwarzacz za pomocą najnowszych wersji aparatu Unity.

## <a name="41010"></a>4.10.1.0
Wydany 11 maja 2021 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązano problemy ze stabilnością w [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md) przypadku szybkiej poprawki.

  - Rozwiązano problemy z wydajnością wątków.

## <a name="41000"></a>4.10.0.0
Wydana 13 kwietnia 2021 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano [`UNT0019`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0019.md) diagnostykę. Niepotrzebne wywołanie pośrednie dla `GameObject.gameObject` .

  - Dodano [`UNT0020`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0020.md) diagnostykę. `MenuItem` atrybut używany w metodzie niestatycznej.

  - Dodano [`UNT0021`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0021.md) diagnostykę. Komunikat aparatu Unity powinien być chroniony (opcjonalnie).

  - Dodano [`UNT0022`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0022.md) diagnostykę. Nieefektywna metoda ustawienia pozycji i obrotu.

  - Dodano [`UNT0023`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0023.md) diagnostykę. Coalescing assignment on Unity objects (Coalescing assignment on Unity objects )).

  - Dodano [`USP0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0017.md) suppressor dla `IDE0074` . Obiekty aparatu Unity nie powinny używać przypisania coalescing.

  - Dodano wykrywanie niesprzyjających projektów języka C# przeznaczonych dla aparatu Unity.

  - Dodano wyszukiwanie odwoływać się do zasobów aparatu Unity w funkcji CodeLens.

## <a name="4910"></a>4.9.1.0
Wydana 2 marca 2021 r.

### <a name="new-features"></a>Nowe funkcje

- **Oceny:**

  - Dodano `Active Scene` do lokalizacji lokalnych z obiektami gry głównej.

  - Dodano `this.gameObject` ją do lokalizacji lokalnych, ponieważ jest szeroko używana w projektach aparatu Unity.

  - Dodano `Children` grupy i do wszystkich wystąpień, aby można było łatwo wyświetlić całą `Components` `GameObject` hierarchię obiektów.

  - Dodano `Scene Path` do `GameObject` wszystkich wystąpień, aby pokazać lokalizację w scenie.

  - Dodano obsługę `JobEntityBatch` /lambdas w przypadku używania jednostek z generatorami źródła.

  - Ulepszono obsługę wyświetlania dużych tablic (przy użyciu zasobników indeksów).
  
  - Dodano brakujące komunikaty aparatu Unity dla interfejsu API 2019.4.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązano różne problemy z interfejsem użytkownika w językach innych niż ENU.

  - Rozwiązano problemy ze stabilnością w [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) diagnostyce.
  
- **Debugowania:**

  - Rozwiązano problemy z rozłączaniem maszyny wirtualnej podczas korzystania z `Trace` metod.

- **Oceny:**

  - Naprawiono filtrowanie przestarzałych właściwości, które zgłaszały wyjątki.

## <a name="4900"></a>4.9.0.0
Wydany 20 stycznia 2021 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę `raytrace shaders` plików `UXML` i `USS` .

  - Dodano `.vsconfig` obsługę generowania. Visual Studio wykryć brakujące składniki i monitować o ich zainstalowanie podczas korzystania z projektów aparatu Unity.

  - Zaktualizowano interfejs API komunikatów aparatu Unity (dla wszystkich metod używanych jako coroutines).

  - Zaktualizowano Android SDK wykrywania zagrożeń.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono odświeżanie procesu podczas korzystania z okna dialogowego wyboru wystąpienia.

  - Naprawiono [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) diagnostykę, która wywoływała nieprawidłowe ostrzeżenia dotyczące coroutines i `AssetPostprocessor.OnAssignMaterialModel` .

## <a name="4820"></a>4.8.2.0
Wydany 10 listopada 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Ulepszono [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md) diagnostykę w celu zastosowania do wszystkich dziedziczące z `Component` , a nie tylko `MonoBehaviour` .

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono unieważnienie komunikatu CodeLens.

## <a name="4810"></a>4.8.1.0
Wydany 13 października 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Oceny:**

  - Dodano obsługę niejawnej konwersji za pomocą wywołania. Wcześniej ewaluator wymuszał ścisłe sprawdzanie typów, co było wynikiem `Failed to find a match for method([parameters...])` komunikatów ostrzegawczych.

- **Integracji:**

  - Dodano [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) diagnostykę. Nie należy używać funkcji `System.Reflection` w komunikatach o krytycznym znaczeniu dla `Update` wydajności, takich `FixedUpdate` jak , , `LateUpdate` lub `OnGUI` .

  - Ulepszone [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) i [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) pomijacze z obsługą wszystkich `AssetPostprocessor` metod statycznych.

  - Dodano [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md) suppressor dla `CS8618` . `C# 8.0` wprowadzono typy referencyjne dopuszczane wartością null i typy referencyjne, które nie mogą dopuszczać wartości null. Wykrywanie inicjalizacji typów dziedziczonych z `UnityEngine.Object` metody nie jest obsługiwane i spowoduje błędy.

  - Teraz przy użyciu tego samego odtwarzacza i mechanizmu generowania projektu asmdef dla aparatu Unity 2019.x i 2020.x+.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono nieoczekiwane uzupełnianie komunikatów w komentarzach.

## <a name="4800"></a>4.8.0.0 
Wydana 14 września 2020 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono generowanie projektu odtwarzacza za pomocą aparatu Unity 2019.x.

## <a name="4710"></a>4.7.1.0
Wydana 5 sierpnia 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę przestrzeni nazw do szablonów domyślnych.
  
  - Zaktualizowano interfejs API komunikatów aparatu Unity do wersji 2019.4.

  - Dodano [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) suppressor dla `CA1823` . Pola prywatne z `SerializeField` atrybutami lub `SerializeReference` nie powinny być oznaczone jako nieużywane (FxCop).
  
  - Dodano [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) suppressor dla `CA1822` . Komunikaty aparatu Unity nie powinny być oflagowane jako kandydaci `static` do modyfikatora (FxCop).

  - Dodano [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) suppressor dla `CA1801` . Nieużywanych parametrów nie należy usuwać z komunikatów aparatu Unity (FxCop).
  
  - Dodano obsługę elementu MenuItem do [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) suppressor.  

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) metody i pomijały, które nie działają z [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) dodatkowymi nawiasami ani argumentami metody.
  
  - Naprawiono obowiązkowe odświeżanie bazy danych zasobów nawet wtedy, gdy automatyczne odświeżanie zostało wyłączone w ustawieniach aparatu Unity.

## <a name="4700"></a>4.7.0.0
Wydany 23 czerwca 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę utrwalania folderów rozwiązań, gdy unity ponownie generuje rozwiązanie i projekty.

  - Dodano [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) diagnostykę. Wykryj niepoprawny podpis metody za pomocą `InitializeOnLoadMethod` atrybutu `RuntimeInitializeOnLoadMethod` lub .

  - Dodano [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) diagnostykę. Użycie `Invoke` , lub z pierwszym `InvokeRepeating` `StartCoroutine` `StopCoroutine` argumentem jako literału ciągu nie jest bezpieczne pod typem.

  - Dodano [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) diagnostykę. `SetPixels` wywołania jest powolne.

  - Dodano obsługę komentarza blokowego i wcięcia dla plików cieniowania.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Nie resetuj zaznaczenia podczas filtrowania komunikatów w kreatorze komunikatów aparatu Unity.
  
  - Zawsze używaj domyślnej przeglądarki podczas otwierania dokumentacji interfejsu API aparatu Unity.
  
  - Naprawiono pomijanie , i z następującymi [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) regułami: [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) pomijanie (tylko do odczytu), (nieużywane), (nigdy przypisane) dla wszystkich pól dekorowanych `IDE0044` `IDE0051` `CS0649` atrybutem SerializeField. Pomijaj element `CS0649` (nigdy nieprzypisane) dla pól publicznych wszystkich typów rozszerzających elementy `Unity.Object`.

  - Naprawiono sprawdzanie parametrów typu ogólnego dla [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) diagostycznego.

- **Oceny:**

  - Naprawiono porównanie równości z wylikami.

## <a name="4610"></a>4.6.1.0
Wydany 19 maja 2020 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Ostrzegaj, jeśli nie możemy utworzyć serwera obsługi komunikatów po stronie aparatu Unity.
  
  - Prawidłowo uruchamiaj analizatory podczas uproszczonej kompilacji.
  
  - Rozwiązaliśmy problem, który miał miejsce, gdy klasa MonoBehaviour utworzona na podstawie upe nie była dopasowana do nazwy pliku.

## <a name="4600"></a>4.6.0.0
Wydana 14 kwietnia 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę codeLens (skryptów i komunikatów aparatu Unity).
  
  - Dodano [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) diagnostykę. Wykrywanie i zawijanie wywołań do coroutines w `StartCoroutine()` .

  - Dodano [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) diagnostykę. Wykryj i usuń nieprawidłowy lub nadmiarowy `SerializeField` atrybut.

  - Dodano [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) diagnostykę. Wykryj `GetComponent()` wywołaną z typem nieskładnikowym lub bez interfejsu.
  
  - Dodano [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) suppressor dla `IDE0051` . Nie oznaczaj metod za pomocą `ContextMenu` atrybutu lub przywołyowanych przez pole z `ContextMenuItem` atrybutem jako nieużywane.

  - Dodano [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) suppressor dla `IDE0051` . Nie flaguj pól z `ContextMenuItem` atrybutem jako nieużywane.
  
  - Dodano [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) suppressor dla `IDE0044` . Nie należy pól z `ContextMenuItem` atrybutem tylko do odczytu.
  
  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md)Wartości [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) , i działają teraz dla atrybutów i [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) `SerializeReference` `SerializeField` .
  
### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Polecenia uruchamiania/zatrzymania wysyłaj do aparatu Unity tylko wtedy, gdy edytor może się komunikować.
  
  - Naprawiono dokumentację szybkich informacji z odziedziczoną wiadomością.
  
  - Naprawiono zakres `CreateInspectorGUI` komunikatów.

  - Nie zgłaszaj [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) metod za pomocą modyfikatorów polimorficznych.

- **Oceny:**

  - Naprawiono obsługę aliasowanych using.

## <a name="4510"></a>4.5.1.0

Wydana 16 marca 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) suppressor dla `IDE0051` . Metody prywatne używane z metodami Invoke, InvokeRepeating, StartCoroutine lub StopCoroutine nie powinny być oznaczone jako nieużywane.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono dokumentację OnDrawGizmos/OnDrawgizmosSelected.

- **Oceny:**

  - Naprawiono inspekcję argumentów lambda.

## <a name="4501"></a>4.5.0.1

Wydany 19 lutego 2020 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) sprawdzanie diagnostyczne pod celu sprawdzenia, czy podpis komunikatu jest nieprawidłowy. Podczas inspekcji typów z wieloma poziomami dziedziczenia ta diagnostyka może się nie powieść z następującym komunikatem: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="4500"></a>4.5.0.0

Wydany 22 stycznia 2020 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę plików HLSL.
  
  - Dodano [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) suppressor dla `IDE0051` . Pola prywatne z `SerializeField` atrybutem nie powinny być oznaczone jako nieużywane.
  
  - Dodano [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) suppressor dla `CS0649` . Pola z `SerializeField` atrybutem nie powinny być oznaczone jako nieprzypisane.  

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono generowanie projektu `GenerateTargetFrameworkMonikerAttribute` (element docelowy nie zawsze był poprawnie zlokalizowany).

## <a name="4420"></a>4.4.2.0

Wydany 3 grudnia 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono diagnostykę za pomocą interfejsów zdefiniowanych przez użytkownika.

  - Naprawiono szybkie etykietki narzędzi z źle sformułowanych wyrażeniami.

## <a name="4410"></a>4.4.1.0

Wydany 6 listopada 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę procesów w tle aparatu Unity. (Debuger może automatycznie łączyć się z procesem głównym, a nie z procesem podrzędnym).
  
  - Dodano szybką etykietkę narzędzia dla komunikatów aparatu Unity z wyświetloną skojarzoną dokumentacją.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono analizator porównania tagów [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md) z zaawansowanymi wyrażeniami binarnymi i wywołaniami.

### <a name="deprecated-features"></a>Przestarzałe funkcje

- **Integracji:**

  - W przyszłości Visual Studio Tools for Unity będą obsługiwać tylko Visual Studio 2017+.

## <a name="4400"></a>4.4.0.0

Wydany 15 października 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) suppressor dla `IDE0060` (nieużywanego parametru) dla wszystkich komunikatów aparatu Unity.
  
  - Dodano szybką etykietkę narzędzia dla pól oznaczonych tagiem `TooltipAttribute` . (Będzie to również działać w przypadku prostego uzyskiwania dostępu przy użyciu tego pola).

## <a name="4330"></a>4.3.3.0

Wydany 23 września 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono raportowanie błędów i ostrzeżeń dla lekkich kompilacji.

## <a name="4320"></a>4.3.2.0

Wydany 16 września 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Pogłębiliśmy wiedzę o tym, że program Visual Studio dla projektów Unity, dodając nową diagnostykę specyficzną dla aparatu Unity. Wprowadziliśmy również zmiany powodujące, że środowisko IDE działa teraz bardziej inteligentnie dzięki pomijaniu ogólnej diagnostyki języka C#, która nie dotyczy projektów Unity. Na przykład w ide nie będzie pokazywana szybka poprawka w celu zmiany zmiennej inspektora, co uniemożliwiłoby zmodyfikowanie zmiennej w `readonly` edytorze aparatu Unity.
    - [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md): komunikaty aparatu Unity są wywoływane przez środowisko uruchomieniowe, nawet jeśli są puste, nie deklaruj ich, aby uniknąć niesprawdowego przetwarzania przez środowisko uruchomieniowe aparatu Unity.
    - [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md): porównanie tagów przy użyciu równości ciągów jest wolniejsze niż wbudowana metoda CompareTag.
    - [`UNT0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0003.md): Użycie ogólnej formy metody GetComponent jest preferowane ze względu na bezpieczeństwo typu.
    - [`UNT0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0004.md): Komunikat aktualizacji jest zależny od szybkości ramki i powinien używać wartości Time.deltaTime zamiast Time.fixedDeltaTime.
    - [`UNT0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0005.md): Komunikat FixedUpdate jest niezależny od szybkości ramki i powinien używać wartości Time.fixedDeltaTime zamiast Time.deltaTime.
    - [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md): wykryto niepoprawną sygnaturę metody dla tego komunikatu aparatu Unity.
    - [`UNT0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0007.md): Unity przesłania operator porównania wartości null dla obiektów Unity, które są niezgodne z ujągnięciem wartości null.
    - [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md): Unity zastępuje operator porównania wartości null dla obiektów Unity, które są niezgodne z propagacja wartości null.
    - [`UNT0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0009.md): Podczas stosowania atrybutu InitializeOnLoad do klasy należy podać konstruktor statyczny. Atrybut InitializeOnLoad zapewnia, że zostanie on wywołany podczas uruchamiania edytora.
    - [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md): Składniki MonoBehaviour powinny być tworzone tylko przy użyciu funkcji AddComponent(). MonoBehaviour to składnik, który musi zostać dołączony do obiektu GameObject.
    - [`UNT0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0011.md): ScriptableObject należy tworzyć tylko przy użyciu funkcji CreateInstance(). Obiekt ScriptableObject musi zostać utworzony przez aparat Unity do obsługi metod komunikatów aparatu Unity.
    - [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) dla `IDE0029` : Obiekty aparatu Unity nie powinny używać funkcji coalescing o wartości null.
    - [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) dla `IDE0031` : Obiekty unity nie powinny używać propagacji wartości null.
    - [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) for `IDE0051` : komunikaty aparatu Unity są wywoływane przez środowisko uruchomieniowe aparatu Unity.
    - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) dla `IDE0044` : Pola z atrybutem SerializeField nie powinny być tylko do odczytu.

## <a name="4310"></a>4.3.1.0

Wydany 4 września 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Oceny:**

  - Dodano obsługę lepszego wyświetlania typu, tj. `List<object>` zamiast `List'1[[System.Object, <corlib...>]]` .

  - Dodano obsługę dostępu do wskaźnika członkowskiego, `p->data->member` tj. .

  - Dodano obsługę niejawnych konwersji w inicjatorach tablic, `new byte [] {1,2,3,4}` tj. .

## <a name="4300"></a>4.3.0.0

Wydany 13 sierpnia 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Dodano obsługę protokołu MDS 2.51.

- **Integracji:**

  - Ulepszono okno "Dołączanie do wystąpienia aparatu Unity" za pomocą funkcji sortowania, wyszukiwania i odświeżania. Identyfikator PID jest teraz wyświetlany nawet w przypadku odtwarzaczy lokalnych (przez odpytanie gniazd nasłuchiwania w systemie w celu pobrania procesu właścicielu).

  - Dodano obsługę plików asmdef.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono obsługę źle sformułowanych komunikatów podczas komunikacji z odtwarzaczami Unity.

- **Oceny:**

  - Naprawiono obsługę przestrzeni nazw w wyrażeniach.

  - Naprawiono inspekcję typów IntPtr.
  
  - Rozwiązano problemy z wykonywaniem krok po kroku z wyjątkami.

  - Naprawiono ocenę identyfikatorów pseudo (takich jak $exception).

  - Zapobiegaj awarii podczas wyłuskania nieprawidłowych adresów.  

  - Rozwiązano problem z niezaładowanych domen aplikacji.

## <a name="4201"></a>4.2.0.1

Wydany 24 lipca 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano nową opcję tworzenia plików dowolnego typu z eksploratora projektów aparatu Unity.
  
  - Ulepszanie buforowania diagnostycznego w przypadku korzystania z szybkich kompilacji dla projektów unity.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązano problem, który dotyczył tego, że rozszerzenie pliku nie było obsługiwane przez żaden dobrze znany edytor.

  - Naprawiono obsługę rozszerzeń niestandardowych w eksploratorze projektów aparatu Unity.

  - Naprawiono ustawienia zapisywania poza głównym oknem dialogowym.

  - Usunięto starszą zależność Microsoft.VisualStudio.MPF.

## <a name="4110"></a>4.1.1.0

Wydany 24 maja 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Zaktualizowano interfejs API MonoBehaviour do wersji 2019.1.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono ostrzeżenia i błędy raportowania w danych wyjściowych po włączeniu uproszczonej kompilacji.

  - Poprawiono uproszczone działanie kompilacji.

## <a name="4100"></a>4.1.0.0

Wydany 21 maja 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę nowego interfejsu API wsadowego w celu szybszego ponownego ładowania projektów.

  - Wyłączono pełną kompilację dla projektów Unity na rzecz używania błędów i ostrzeżeń funkcji IntelliSense. W rzeczywistości unity tworzy Visual Studio z projektami biblioteki klas, które reprezentują to, co unity robi wewnętrznie. Oznacza to, że wynik kompilacji w programie Visual Studio nigdy nie jest używany ani odbierany przez aparatu Unity, ponieważ ich potok kompilacji jest zamknięty. Tworzenie w Visual Studio po prostu zużywa zasoby bez żadnych zasobów. Jeśli potrzebujesz pełnej kompilacji, ponieważ masz narzędzia lub konfigurację, która od niego zależy, możesz wyłączyć tę optymalizację (Narzędzia/Opcje/Narzędzia dla aparatu Unity/Wyłącz pełną kompilację projektów).

  - Automatycznie wyświetla eksplorator projektów aparatu Unity (UPE) po załadowaniu projektu aparatu Unity. UpE zostanie zadokowana obok Eksplorator rozwiązań.

  - Zaktualizowano mechanizm wyodrębniania nazw projektów za pomocą aparatu Unity 2019.x.

  - Dodano obsługę pakietów aparatu Unity w upe. Widoczne są tylko pakiety, do których istnieją odwołania (przy użyciu manifest.jsw folderze ) i Pakiety `Packages` lokalne (osadzone w `Packages` folderze ).

- **Generowanie projektu:**

  - Zachowaj właściwości zewnętrzne podczas przetwarzania pliku rozwiązania.

- **Oceny:**

  - Dodano obsługę nazw kwalifikowanych przez alias (na razie tylko globalnej przestrzeni nazw). Dlatego ewaluator wyrażeń akceptuje teraz typy przy użyciu formularza global::namespace.type.

  - Dodano obsługę `pointer[index]` formularza, który jest semantycznie identyczny z formularzem wyłuskania `*(pointer+index)` wskaźnika.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązano problemy z zależnościami w pliku Microsoft.VisualStudio.MPF.

  - Naprawiono dołączanie odtwarzacza platformy uniwersalnej systemu Windows bez załadowanego projektu.

  - Naprawiono automatyczne odświeżanie bazy danych zasobów, Visual Studio nie zostało jeszcze dołączone.

  - Rozwiązano problemy z motywami związane z etykietami i polami wyboru.

- **Debuger:**

  - Naprawiono wykonywanie krokowe przy użyciu konstruktorów statycznych.

## <a name="4005"></a>4.0.0.5

Wydany 27 lutego 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono Visual Studio wykrywania wersji za pomocą pakietu instalacyjnego.

  - Usunięto nieużywane zestawy z pakietu instalacyjnego.

## <a name="4004"></a>4.0.0.4

Wydany 13 lutego 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę prawidłowego wykrywania procesów aparatu Unity podczas instalacji i umożliwienia aparatowi instalacji lepszej obsługi blokad plików.

  - Zaktualizowano `ScriptableObject` interfejs API.

## <a name="4003"></a>4.0.0.3

Wydany 31 stycznia 2019 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Pola publiczne i serializowane nie będą już powodować ostrzeżeń. W projektach aparatu Unity automatycznie pominięto ostrzeżenia `CS0649` kompilatora i `IDE0051` , które utworzyły te komunikaty.

- **Integracji:**

  - Ulepszono środowisko użytkownika do wyświetlania wystąpień edytora i odtwarzacza aparatu Unity (okna można teraz zmieniać, używać jednolitych marginesów i wyświetlać uchwyt zmiany rozmiaru). Dodano Process-Id dla edytorów aparatu Unity.

  - Zaktualizowano `MonoBehaviour` interfejs API.

- **Oceny:**

  - Dodano obsługę funkcji lokalnych.

  - Dodano obsługę zmiennych pseudo (identyfikatorów wyjątków i obiektów).

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązano problem z obrazami i motywami moniker.

  - Zapisuj tylko do Okno Dane wyjściowe podczas debugowania, podczas automatycznego odświeżania bazy danych zasobów.

  - Naprawiono opóźnienia interfejsu użytkownika podczas filtrowania w kreatorze MonoBehaviour.

- **Debuger:**

  - Naprawiono odczytywanie atrybutu niestandardowego dla argumentów nazwanych w przypadku używania starych wersji protokołu.

## <a name="4002"></a>4.0.0.2

Wydany 23 stycznia 2019 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono eksperymentalne generowanie kompilacji.

  - Naprawiono obsługę zdarzeń pliku projektu w celu zminimalizowania nacisku wątku interfejsu użytkownika.

  - Naprawiono dostawcę uzupełniania ze zmianami tekstu wsadowego.

- **Debuger:**

  - Naprawiono wyświetlanie komunikatów debugowania użytkownika w dołączonym debugerze.

## <a name="4001"></a>4.0.0.1

Wydany 10 grudnia 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Oceny:**

  - Zastąpiono NRefactory na rzecz roslyn w celu oceny wyrażeń.

  - Dodano obsługę wskaźników: wyłuskanie, rzutowanie i arytmetyka wskaźnika (w tym celu wymagane jest zarówno środowisko Unity 2018.2+, jak i nowe środowisko uruchomieniowe).

  - Dodano obsługę widoku wskaźnika tablicy (np. w języku C++). Weź wyrażenie wskaźnika, a następnie dołącz przecinek i liczbę elementów, które chcesz zobaczyć.

  - Dodano obsługę konstrukcji asynchronicznych.

- **Integracji:**

  - Dodano obsługę automatycznego odświeżania bazy danych zasobów aparatu Unity po zapisaniu. Ta funkcja jest domyślnie włączona i spowoduje wyzwolenie ponownej kompilacji po stronie aparatu Unity podczas zapisywania skryptu w Visual Studio. Możesz wyłączyć tę funkcję w menu Tools\Options\Tools for Unity\Refresh Unity's AssetDatabase on save (Narzędzia\Opcje\Narzędzia dla aparatu Unity\Odśwież bazę danych AssetDatabase aparatu Unity przy zapisywaniu).

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono aktywację mostka, Visual Studio nie była wybierana jako preferowany edytor zewnętrzny.

  - Naprawiono ocenę wyrażeń w przypadku źle sformułowanych lub nieobsługiwanych wyrażeń.

## <a name="4000"></a>4.0.0.0

Wydany 4 grudnia 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Dodano obsługę Visual Studio 2019 (aby móc używać systemu Visual Studio 2019 jako zewnętrznego edytora skryptów, potrzebujesz co najmniej aparatu Unity 2018.3).

  - Przyjęto usługę Visual Studio obrazów i katalog obrazów, z pełną obsługą skalowania HDPI, idealnych obrazów pikseli i o treści.

### <a name="deprecated-features"></a>Przestarzałe funkcje

- **Integracji:**

  - W przyszłości Visual Studio Tools for Unity będzie obsługiwać tylko unity 5.2+ (z wbudowaną integracją Visual Studio Unity).

  - W przyszłości Visual Studio Tools for Unity będą obsługiwać tylko Visual Studio 2015+.

  - Usunięto starszą usługę językową, listę błędów i pasek stanu.

  - Usunięto szybki kreator monobehaviour (na rzecz dedykowanej obsługi funkcji IntelliSense).

## <a name="3903"></a>3.9.0.3

Wydana 28 listopada 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązano problemy z ponownym ładowaniem projektu i intellisense podczas dodawania lub usuwania skryptów znajdujących się w pierwszym projekcie.

## <a name="3902"></a>3.9.0.2

Wydany 19 listopada 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Naprawiono zakleszczenie w bibliotece używane do komunikowania się z aparatem debugera aparatu Unity, co powoduje zablokowanie aparatu Visual Studio lub Unity, szczególnie w przypadku trafienia przycisku "Dołącz do aparatu Unity" lub ponownego uruchomienia gry.

## <a name="3901"></a>3.9.0.1

Wydany 15 listopada 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono aktywację wtyczki aparatu Unity po wybraniu innego edytora domyślnego.

## <a name="3900"></a>3.9.0.0

Wydany 13 listopada 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Wycofano obejście błędu wydajności aparatu Unity, który został naprawiony przez unity.

## <a name="3807"></a>3.8.0.7

Wydana 20 września 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - (Przyniesiene z 3.9.0.2) Naprawiono zakleszczenie w bibliotece używane do komunikowania się z aparatem debugera aparatu Unity, co powoduje zablokowanie aparatu Visual Studio lub Unity, szczególnie w przypadku trafienia przycisku "Dołącz do aparatu Unity" lub ponownego uruchomienia gry.

## <a name="3806"></a>3.8.0.6

Wydana 27 sierpnia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono ponowne ładowanie projektów i rozwiązania.

## <a name="3805"></a>3.8.0.5

Wydana 20 sierpnia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono usuwanie subskrypcji monitorowania projektu.

## <a name="3804"></a>3.8.0.4

Wydana 14 sierpnia 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Oceny:**

  - Dodano obsługę wartości wskaźnika.

  - Dodano obsługę metod ogólnych.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Inteligentne ponowne ładowanie z wieloma projektami uległo zmianie.

## <a name="3803"></a>3.8.0.3

Wydany 24 lipca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - (Przyniesiene z powrotem z 3.9.0.0) Wycofano obejście błędu wydajności aparatu Unity, który został naprawiony przez unity.

## <a name="3802"></a>3.8.0.2

Wydany 7 lipca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Przejściowe obejście błędu wydajności aparatu Unity: buforowanie rozwiązania MonoIslands podczas generowania projektów.

## <a name="3801"></a>3.8.0.1

Wydany 26 czerwca 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Debugowania:**

  - Dodano obsługę poleceń UserLog i UserBreak.

  - Dodano obsługę ładowania typu z opóźnieniem (optymalizacja obciążenia sieciowego i opóźnienia odpowiedzi debugera).

### <a name="bug-fixes"></a>Poprawki błędów

- **Oceny:**

  - Ulepszona ocena wyrażeń operatora binarnego i wyszukiwanie metod.

## <a name="3800"></a>3.8.0.0

Wydany 30 maja 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Debugowania:**

  - Dodano obsługę wyświetlania zmiennych w konstrukcjach asynchronicznych.

  - Dodano obsługę przetwarzania zagnieżdżonych typów podczas ustawiania punktów przerwania w celu zapobiegania ostrzeżeń za pomocą konstrukcji kompilatora.

- **Integracji:**

  - Dodano obsługę gramatyki tekstu dla cieniowania (obciążenie języka C++ nie jest już potrzebne do kolorowania kodu cieniowania).

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Nie należy już konwertować przenośnego pliku pdb na mdb podczas korzystania z nowego środowiska uruchomieniowego aparatu Unity.

## <a name="3701"></a>3.7.0.1

Wydany 7 maja 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Instalator:**

  - Rozwiązano problem z zależnością podczas korzystania z kompilacji eksperymentalnych.

## <a name="3700"></a>3.7.0.0

Wydany 7 maja 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Debugowania:**

  - Dodano obsługę orkiestracji debugowania (debugowanie wielu odtwarzaczy/edytora przy użyciu tej samej Visual Studio sesji).

  - Dodano obsługę debugowania odtwarzacza USB systemu Android.

  - Dodano obsługę debugowania odtwarzacza UWP/IL2CPP.

- **Oceny:**

  - Dodano obsługę specyfikatorów szesnastkowych.

  - Ulepszone środowisko oceny okna zegarka.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono użycie ustawień wyjątków.

- **Generowanie projektu:**

  - Wyklucz jednostki kompilacji menedżera pakietów z generowania.

## <a name="3605"></a>3.6.0.5

Wydana 13 marca 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę nowego generatora projektu w a aparatu Unity 2018.1.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono obsługę uszkodzonych stanów w projektach niestandardowych.

- **Debuger:**

  - Naprawiono ustawienie następnej instrukcji .

## <a name="3604"></a>3.6.0.4

Wydana 5 marca 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono wykrywanie wersji mono.

- **Integracji:**

  - Rozwiązano problemy z chronometrażu w 2018.1 i aktywacji wtyczki.

## <a name="3603"></a>3.6.0.3

Wydany 23 lutego 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę .NET Standard.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono wykrywanie docelowej struktury aparatu Unity.

- **Debuger:**

  - Naprawiono przerywanie wyjątków zgłaszanych poza kodem użytkownika.

## <a name="3602"></a>3.6.0.2

Wydany 7 lutego 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Zaktualizuj powierzchnię interfejsu API UnityMessage dla wersji 2017.3.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Załaduj ponownie projekty tylko w przypadku zmiany zewnętrznej (z ograniczaniem przepustowości).

## <a name="3601"></a>3.6.0.1

Wydany 24 stycznia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono automatyczną konwersję symboli debugowania pdb do mdb.

  - Naprawiono pośrednie wywołanie funkcji EditorPrefs.GetBool wpływające na inspektora podczas próby zmiany rozmiaru tablicy.

## <a name="3600"></a>3.6.0.0

Wydana 10 stycznia 2018 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę modelu referencyjnego MonoIsland 2018.1.

- **Oceny:**

  - Dodano obsługę $exception identyfikatora.

- **Debuger:**

  - Dodano obsługę atrybutów DebuggerHidden/DebuggerStepThrough w nowym środowisku uruchomieniowym aparatu Unity.

- **Kreatorów:**

  - Wprowadzenie najnowszej wersji dla kreatorów.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono obliczanie identyfikatora GUID projektu dla projektów odtwarzacza.

- **Debuger:**

  - Rozwiązano problem z wyścigiem w obsłudze zdarzeń trwałych.

- **Kreatorów:**

  - Odśwież kontekst roslyn przed wstawianiem metody.

## <a name="3503"></a>3.5.0.3

Wydana 9 stycznia 2018 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Naprawiono automatyczną konwersję symboli debugowania pdb do mdb.

## <a name="3502"></a>3.5.0.2

Wydana 4 grudnia 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Integracji:**

  - Projekty Unity są teraz automatycznie ponownie ładowane w programie Visual Studio po dodaniu skryptu do środowiska Unity lub jego usunięciu.

- **Debuger:**

  - Dodano opcję używania debugera Mono udostępnionego przez platformę Xamarin i Visual Studio dla komputerów Mac debugowania edytora aparatu Unity.

  - Dodano obsługę przenośnych plików symboli debugowania.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracji:**

  - Rozwiązano problemy z zależnościami konfiguracji.

  - Rozwiązano problem: menu pomocy interfejsu API aparatu Unity nie jest wyświetlane.

- **Generowanie projektu:**

  - Naprawiono generowanie projektu odtwarzacza podczas pracy z grami platformy uniwersalnej systemu Windows przy użyciu zaplecza IL2CPP/.NET 4.6.

  - Naprawiono dodatkowe .dll błędnie dodane do nazwy pliku zestawu.

  - Naprawiono użycie określonego poziomu zgodności interfejsu API projektu zamiast poziomu globalnego.

  - Nie wymuszaj flagi AllowAttachedDebuggingOfEditor Unity, ponieważ wartość domyślna to teraz "true".

## <a name="3402"></a>3.4.0.2

Wydana 19 września 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę assembly.jsw jednostkach kompilacji.

  - Zatrzymano kopiowanie zestawów unity do folderu projektu.

- **Debuger:**

  - Dodano obsługę ustawiania następnej instrukcji przy użyciu nowego środowiska uruchomieniowego aparatu Unity.

  - Dodano obsługę typu dziesiętnego w nowym środowisku uruchomieniowym aparatu Unity.

  - Dodano obsługę konwersji niejawnych/jawnych.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oceny:**

  - Naprawiono tworzenie tablicy z niejawnym rozmiarem.

  - Naprawiono elementy generowane przez kompilator z elementami lokalnymi.

- **Generowanie projektu:**

  - Naprawiono odwołanie do Microsoft.CSharp na poziomie interfejsu API w wersji 4.6.

## <a name="3302"></a>3.3.0.2

Wydana 15 sierpnia 2017 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono generowanie Visual Studio na platformie Unity 5.5 i poprzednich wersjach.

## <a name="3300"></a>3.3.0.0

Wydana 14 sierpnia 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Oceny:**

  - Dodano obsługę tworzenia struktur przy użyciu nowego środowiska uruchomieniowego aparatu Unity.

  - Dodano obsługę wskaźników w formie odtąd.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oceny:**

  - Naprawiono wywołania metody w elementach pierwotnych.

  - Naprawiono ocenę pól z typami oznaczonymi za pomocą wartości BeforeFieldInit.

  - Naprawiono nie obsługiwane wywołania z operatorami binarnymi (podciągiem).

  - Rozwiązano problemy podczas dodawania elementów do Visual Studio Watch.

- **Generowanie projektu:**

  - Naprawiono odwołania do nazw zestawu w plikach mcs.rsp.

  - Naprawiono definicje z poziomami interfejsu API.

## <a name="3200"></a>3.2.0.0

Wydana 10 maja 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Instalator:**

  - Dodano obsługę czyszczenia pamięci podręcznej MEF.

### <a name="bug-fixes"></a>Poprawki błędów

- **Edytor kodu:**

  - Naprawiono klasyfikację/uzupełnianie za pomocą atrybutów niestandardowych.

  - Naprawiono migotowanie komunikatów aparatu Unity.

## <a name="3100"></a>3.1.0.0

Wydana 7 kwietnia 2017 r.

### <a name="new-features"></a>Nowe funkcje

- **Debuger:**

  - Dodano obsługę nowego środowiska uruchomieniowego aparatu Unity (ze zgodnością z platformą .NET 4.6 / C# 6).

- **Generowanie projektu:**

  - Dodano obsługę profilu .NET 4.6.

  - Dodano obsługę plików mcs.rsp.

  - Zawsze włączaj niebezpieczny przełącznik kompilacji, gdy jest używane unity 5.6.

  - Dodano obsługę generowania projektu "Player" podczas korzystania z platformy Sklepu Windows i zaplecza il2cpp.

### <a name="bug-fixes"></a>Poprawki błędów

- **Edytor kodu:**

  - Poprawiono położenie cyka po wstawieniu metody z automatycznym uzupełnianiem.

- **Generowanie projektu:**

  - Usunięto wersję zestawu po przetworzeniu.

## <a name="3001"></a>3.0.0.1

Wydana 7 marca 2017 r.

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Ta wersja zawiera wszystkie nowe funkcje i poprawki błędów wprowadzone w serii 2.8.x.

## <a name="2820---30-preview-3"></a>2.8.2.0 – 3.0 (wersja zapoznawcza 3)
Wydany 25 stycznia 2017 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono regresję, w której wtyczki projektują się dwukrotnie, najpierw jako binarna biblioteka DLL, a następnie jako odwołanie do projektu.

## <a name="2810---30-preview-2"></a>2.8.1.0 – 3.0 (wersja zapoznawcza 2)
Wydany 23 stycznia 2017 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Edytor kodu:**

  - Usunięto awarię podczas uruchamiania deklaracji atrybutu bez uzupełniania nawiasów klamrowych.

- **Debuger:**

  - Naprawiono punkty przerwania funkcji z coroutines w obszarze nowego kompilatora/środowiska uruchomieniowego aparatu Unity.

  - Dodano ostrzeżenie w przypadku niebindowalnego punktu przerwania (jeśli nie znaleziono odpowiadającej lokalizacji źródłowej).

- **Generowanie projektu:**

  - Naprawiono generowanie csproj ze znakami specjalnymi/zlokalizowanymi.

  - Naprawiono odwołania poza zasobami, takimi jak biblioteka (na przykład zestaw SDK serwisu Facebook).

- **Pozostałe:**

  - Dodano sprawdzanie, aby zapobiec uruchamianiu aparatu Unity podczas instalowania lub odinstalowywania.

  - Przełączyliśmy się na protokół HTTPS w celu ukierunkowania zdalnej dokumentacji aparatu Unity.

## <a name="2800---30-preview"></a>2.8.0.0 – 3.0 (wersja zapoznawcza)
Wydana 17 listopada 2016 r.

### <a name="new-features"></a>Nowe funkcje

- **Ogólne:**

  - Dodano Visual Studio obsługi instalatora programu 2017.

  - Dodano Visual Studio obsługi rozszerzeń programu Visual Studio 2017.

  - Dodano obsługę lokalizacji.

- **Edytor kodu:**

  - Dodano mechanizm IntelliSense dla komunikatów aparatu Unity w języku C#.

  - Dodano kolorowanie kodu w języku C# dla komunikatów unity.

- **Debuger:**

  - Dodano obsługę `is` `as` wyrażeń , , rzutowania bezpośredniego `default` i `new` .

  - Dodano obsługę wyrażeń concat ciągów.

  - Dodano obsługę szesnastkowego wyświetlania wartości całkowitych.

  - Dodano obsługę tworzenia nowych zmiennych tymczasowych (instrukcji).

  - Dodano obsługę niejawnych konwersji pierwotnych.

  - Dodano lepsze komunikaty o błędach, gdy typ jest oczekiwany lub nie znaleziono.

- **Generowanie projektu:**

  - Usunięto sufiks CSharp z nazw projektów.

  - Usunięto odwołanie do pliku obiektów docelowych msbuild całego systemu.

- **Kreatorów:**

  - Dodano obsługę komunikatów aparatu Unity w typach innych niż zachowanie, takich jak Editor lub EditorWindow.

  - Przełączone na roslyn w celu wstrzykiwania i formatowania komunikatów aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

- **Debuger:**

  - Usunięto usterkę, która ulegała awarii aparatu Unity podczas oceny typów ogólnych.

  - Naprawiono obsługę typów dopuszczanych do wartości null.

  - Poprawiono obsługę wylików.

  - Naprawiono obsługę zagnieżdżonych typów elementów członkowskich.

  - Naprawiono dostęp indeksatora kolekcji.

  - Poprawiono obsługę debugowania ramek iteratorów za pomocą nowego kompilatora języka C#.

- **Generowanie projektu:**

  - Usunięto usterkę uniemożliwiającą kompilację podczas określania celu odtwarzacza internetowego aparatu Unity.

  - Usunięto usterkę uniemożliwiającą kompilację podczas kompilowania skryptu z nazwą pliku zakodowaną w Internecie.

## <a name="2300"></a>2.3.0.0

Wydana 14 lipca 2016 r.

### <a name="new-features"></a>Nowe funkcje

- **Ogólne:**

  - Dodano opcję wyłączania dzienników konsoli aparatu Unity Visual Studio liście błędów aplikacji.

  - Dodano opcję zezwalania na modyfikację właściwości wygenerowanego projektu.

- **Debuger:**

  - Dodano wizualizatory ciągów tekstowych, XML, HTML i JSON.

- **Kreatorów:**

  - Dodano brakujące monoBehaviors.

### <a name="bug-fixes"></a>Poprawki błędów

- **Ogólne:**

  - Rozwiązano konflikt z resharper, który uniemożliwiał wyświetlania kontrolek wewnątrz Visual Studio ustawieniach.

  - Rozwiązano konflikt z platformą Xamarin, który uniemożliwiał debugowanie w niektórych przypadkach.

- **Debuger:**

  - Rozwiązano problem, który powodował Visual Studio się zawieszał podczas debugowania.

  - Rozwiązano problem z punktami przerwania funkcji w Visual Studio 2015 r.

  - Rozwiązano kilka problemów z oceną wyrażeń.

## <a name="2200"></a>2.2.0.0

Wydany 4 lutego 2016 r.

### <a name="new-features"></a>Nowe funkcje

- **Kreatorów:**

  - Dodano inteligentne wyszukiwanie w **kreatorze Implementowanie monoBehavior.**

  - Świadomy kontekst kreatorów; Na przykład komunikaty NetworkBehavior są dostępne tylko podczas pracy z networkBehavior.

  - Dodano obsługę komunikatów NetworkBehavior w kreatorach.

- **Interfejsu użytkownika:**

  - Dodano opcję konfigurowania widoczności komunikatów MonoBehavior.

  - Usunięto Visual Studio właściwości, które nie są istotne dla projektów unity.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Naprawiono odwołania do unityengine i UnityEditor w a unity 4.6.

  - Naprawiono generowanie plików projektu, gdy unity działa w OSX.

  - Naprawiono obsługę nazw projektów zawierających znaki hashmark (#).

  - Ograniczone projekty generowane do języka C# 4.

- **Debuger:**

  - Rozwiązano problem z oceną wyrażeń podczas debugowania wewnątrz coroutine aparatu Unity.

  - Rozwiązano problem, który powodował Visual Studio się zawieszał podczas debugowania.

- **Interfejsu użytkownika:**

  - Usunięto niezgodność z rozszerzeniem [Visual Studio Tabs Studio.](https://tabsstudio.com/)

- **Instalator:**

  - Obsługa instalacji na całym komputerze vstu (instalacji dla wszystkich użytkowników) przez tworzenie wpisów rejestru HKLM.

  - Rozwiązano problemy z dezinstalacją vstu, gdy ta sama wersja vstu jest zainstalowana dla wielu różnych wersji Visual Studio. Na przykład gdy zainstalowano zarówno vstu **2015** 2.1.0.0, jak i VSTU **2013** 2.1.0.0.

## <a name="2100"></a>2.1.0.0

Wydana 8 września 2015 r.

### <a name="new-features"></a>Nowe funkcje

- Obsługa aparatu Unity 5.2

### <a name="bug-fixes"></a>Poprawki błędów

- Wyświetlanie elementów menu na platformie Unity < 4.2

- Komunikat o błędzie nie jest już wyświetlany, gdy program Visual Studio blokuje pliki XML IntelliSense.

- Obsługa <> warunkowych punktów przerwania, gdy argument warunkowy nie \<When Changed> jest wartością logiczną.

- Naprawiono odwołania do zestawów UnityEngine i UnityEditor dla aplikacji ze Sklepu Windows.

- Usunięto błąd podczas przechodzenia krok po kroku w debugerze: Nie można krokować, wyjątek ogólny.

- Naprawiono punkty przerwania liczby trafień w Visual Studio 2015 r.

## <a name="2000"></a>2.0.0.0

Wydana 20 lipca 2015 r.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integracja z platformą Unity:**

  - Naprawiono konwersję symboli debugowania utworzonych w programie Visual Studio 2015 podczas importowania biblioteki DLL i jej symboli debugowania (PDB).

  - Zawsze generuj pliki MDB podczas importowania biblioteki DLL i jej symboli debugowania (PDB), z wyjątkiem sytuacji, gdy podano również plik MDB.

  - Naprawiono niesienie katalogu projektu aparatu Unity za pomocą katalogu obj.

  - Naprawiono generowanie odwołań do System.Xml. Link i System.Runtime.Serialization.

  - Dodano obsługę wielu subskrybentów do elementów zaczepienia interfejsu API generowania plików projektu.

  - Zawsze należy ukończyć generowanie pliku projektu, nawet jeśli jeden z plików do wygenerowania jest zablokowany.

  - Dodano obsługę symboli wieloznacznych * w filtrze rozszerzeń podczas określania plików, które mają zostać uwzględnione w projekcie języka C#.

- **Visual Studio integracji:**

  - Rozwiązano problem ze zgodnością z narzędziami Productivity Power Tools.

  - Naprawiono generowanie monobehaviorów wokół zdarzeń i delegujących deklaracje.

- **Debuger:**

  - Rozwiązano problem z potencjalnym zablokowaniem podczas debugowania.

  - Rozwiązano problem, który oznaczał, że w niektórych ramkach stosu nie były wyświetlane lokalne dane.

  - Naprawiono sprawdzanie pustych tablic.

## <a name="1990---20-preview-2"></a>1.9.9.0 – 2.0 (wersja zapoznawcza 2)
Wydana 2 kwietnia 2015 r.

### <a name="new-features"></a>Nowe funkcje

- **Eksplorator projektów aparatu Unity:**

  - Automatyczna zmiana nazwy klasy podczas zmiany nazwy pliku w Eksploratorze projektów aparatu Unity (zobacz **okno dialogowe** Opcje).

  - Automatycznie wybieraj nowo utworzone skrypty w eksploratorze projektów aparatu Unity.

  - Śledzenie aktywnego skryptu w Eksploratorze projektów aparatu Unity (zobacz **okno dialogowe** Opcje).

  - Podwójna synchronizacja Visual Studio Eksplorator rozwiązań (zobacz **okno dialogowe** Opcje).

  - Adoptuj Visual Studio w Eksploratorze projektów aparatu Unity.

- **Debuger:**

  - Wybierz aktywny element docelowy debugowania z listy zapisanych lub ostatnio używanych elementów docelowych debugowania (zobacz **okno dialogowe** Opcje).

  - Tworzenie punktów przerwania funkcji w metodach MonoBehavior i stosowanie ich do wielu klas MonoBehavior.

  - Obsługa polecenia Make Object ID w debugerze.

  - Obsługa liczby trafień punktów przerwania w debugerze.

  - Obsługa wyjątku przerwania w debugerze (eksperymentalne). Zobacz **Okno dialogowe** Opcje).

  - Obsługa tworzenia obiektów i tablic podczas oceniania wyrażeń w debugerze.

  - Obsługa porównywania wartości null podczas oceniania wyrażeń w debugerze.

  - Odfiltruj przestarzałe elementy członkowskie w oknach zegarka debugera.

- **Instalator:**

  - Zoptymalizowana Visual Studio Tools for Unity rejestracji rozszerzenia.

  - Zainstaluj Visual Studio Tools for Unity dla aparatu Unity 5.

- **Dokumentacja:** Zwiększenie wydajności generowania dokumentacji.

- **Kreatorzy:** Obsługa nowych metod MonoBehavior dla unity 4.6 i Unity 5.

- **Unity:** Niebezpieczne flagi wyszukiwania i niestandardowe definicje w plikach RSP podczas generowania plików projektu.

- **Interfejs użytkownika:** Dodano Visual Studio Tools for Unity **opcje konfiguracji** w Visual Studio.

### <a name="bug-fixes"></a>Poprawki błędów

- **Eksplorator projektów aparatu Unity:**

  - Odśwież Eksplorator projektów aparatu Unity po zmianie nazwy plików z Visual Studio Eksplorator rozwiązań.

  - Zachowaj wybory podczas zmieniania nazw plików w Eksploratorze projektów aparatu Unity.

  - Zapobiegaj automatycznemu rozwijaniu i zwijaniu w przypadku dwukrotnego kliknięcia plików w Eksploratorze projektów aparatu Unity.

  - Upewnij się, że nowo wybrane pliki są widoczne w Eksploratorze projektów aparatu Unity.

- **Debuger:**

  - Zapobiegaj zablokowaniu Visual Studio podczas oceniania wyrażeń w debugerze.

  - Upewnij się, że wywołania metod są nasłane we właściwej domenie w debugerze.

- **Jedność:**

  - Popraw lokalizację pliku UnityVS.OpenFile za pomocą aparatu Unity 5.

  - Popraw lokalizację bazy danych pdb2mdb za pomocą aparatu Unity 5.

  - Zapobiegaj możliwemu wyjątkowi podczas generowania pliku projektu.

  - Zapobiegaj możliwemu zablokowaniu podczas uruchamiania aparatu Unity w OSX.

  - Obsługa wyjątków wewnętrznych.

  - Wysyłanie dzienników konsoli aparatu Unity do listy błędów programu VS.

- **Dokumentacja:** Popraw generowanie dokumentacji dla nowej dokumentacji aparatu Unity.

- **Projekt:** Przenieś pliki meta aparatu Unity i zmień ich nazwy w razie potrzeby, nawet w folderach.

- **Kreatorzy:** Popraw kolejność parametrów metody MonoBehavior podczas generowania kodu.

- **Interfejs użytkownika:** Obsługa Visual Studio motywów menu kontekstowego i ikon.

## <a name="1980---20-preview"></a>1.9.8.0 – 2.0 (wersja zapoznawcza)
Wydana 12 listopada 2014 r.

### <a name="new-features"></a>Nowe funkcje

- Obsługa Visual Studio 2015 r.

- Kolorowanie kodu dla cieniowania aparatu Unity w Visual Studio 2015 r.

- Ulepszona wizualizacja wartości podczas debugowania:

  - Lepsza wizualizacja list tablic, list, tablic skrótów i słowników.

  - Pokaż niedostępne elementy członkowskie i statyczne elementy członkowskie jako kategorie w widokach czujki i lokalnych.

  - Ulepszono wyświetlanie właściwości SerializedProperty aparatu Unity w celu oceny tylko pola wartości prawidłowego dla właściwości.

  - Obsługa debugeraDisplayAttribute dla klas i struktur.

  - Obsługa debuggerTypeProxyAttribute.

- Aby wstawić metody MonoBehaviour, należy użyć naszych kreatorów, aby przestrzegać konwencji kodowania użytkownika.

- Implementowanie obsługi szablonów tekstowych czasu kompilacji w projektach generowanych przez aparat UnityVS.

- Implementowanie obsługi zasobów ResX w projektach generowanych przez aparat UnityVS.

- Obsługa otwierania cieniowania w Visual Studio z aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

- Wyczyść gniazda przed rozpoczęciem gry w a aparatu Unity po wyzwoleniu funkcji Attach and Play w Visual Studio. Rozwiązuje to niektóre problemy ze stabilnością połączenia między aparatu Unity i programem VS w przypadku korzystania z dołączania i odtwarzania.

- Unikaj wywoływania metod w interfejsie debugera aparatu skryptów aparatu Unity, które są podatne na blokowanie aparatu Unity. Rozwiązuje to problem z blokowaniem aparatu Unity podczas dołączania debugera.

- Naprawiono wyświetlanie wywołań, gdy symbole nie są dostępne.

- Nie rejestruj wywołania zwrotnego dziennika, jeśli nie musimy tego robić.

## <a name="1920"></a>1.9.2.0

Wydana 9 października 2014 r.

### <a name="new-features"></a>Nowe funkcje

- Usprawnij wykrywanie odtwarzaczy Unity.

- Podczas korzystania z naszego narzędzia do otwierania plików upewnij się, że unity przekaże numer wiersza, a także nazwę pliku.

- Jeśli nie ma lokalnej dokumentacji, domyślną dokumentacją aparatu Unity w trybie online.

### <a name="bug-fixes"></a>Poprawki błędów

- Napraw potencjalne awarie aparatu Unity po trafieniu punktu przerwania po ponownym załadowaniu domeny.

- Napraw wyjątki wyświetlane w konsoli aparatu Unity podczas zamykania okna Konfiguracja lub Informacje po ponownym załadowaniu domeny.

- Naprawiono wykrywanie 64-bitowego aparatu Unity uruchomionego lokalnie.

- Naprawiono filtrowanie monoBehaviours dla wersji aparatu Unity w kreatorach.

- Naprawiono usterkę, w przypadku której wszystkie zasoby były uwzględniane w plikach projektu, jeśli filtr rozszerzenia był pusty.

## <a name="1910"></a>1.9.1.0

Wydana 22 września 2014 r.

### <a name="new-features"></a>Nowe funkcje

- Optymalizacja punktu przerwania powiązania z lokalizacjami źródłowymi.

- Obsługa przeciążonych metod w ocenie wyrażeń debugera.

- Obsługa typów pierwotnych i wartości boxing w ocenie wyrażeń debugera.

- Obsługa ponownego tworzenia środowiska zmiennych lokalnych języka C# podczas debugowania metod anonimowych.

- Usuń pliki meta i zmień ich nazwy podczas usuwania lub zmieniania nazw plików z Visual Studio.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono obsługę Visual Studio motywów. Wcześniej okna dialogowe w czarnych motywach mogły być wyświetlane jako puste.

- Naprawienie blokowania aparatu Unity podczas nawiązywania połączenia z debugerem podczas ponownego kompilowania aparatu Unity.

- Napraw punkty przerwania podczas debugowania zdalnych edytorów lub odtwarzaczy skompilowanych w innym systemie.

- Naprawienie możliwej Visual Studio awarii po trafieniu punktu przerwania.

- Napraw powiązania punktów przerwania, aby uniknąć wyświetlania punktów przerwania jako niezaładowane.

- Naprawiono obsługę zakresu zmiennych w debugerze, aby uniknąć zmiennych na żywo, które pojawiają się poza zakresem.

- Naprawienie wyszukiwania statycznych elementów członkowskich w ocenie wyrażeń debugera.

- Naprawiono wyświetlanie typów w ocenie wyrażeń debugera w celu wyświetlania statycznych pól i właściwości.

- Naprawiono generowanie rozwiązania, gdy nazwy projektów aparatu Unity zawierają znaki specjalne, Visual Studio zabraniają (problem z #948666).

- Napraw pakiet Visual Studio Tools Unity, aby natychmiast zatrzymać wysyłanie zdarzeń konsoli po usunięciu zaznaczenia opcji (problem z #933357).

- Naprawiono wykrywanie odwołań w celu prawidłowego ponownego generowania odwołań do nowych interfejsów API, takich jak UnityEngine.UI, w projektach generowanych przez aparat UnityVS.

- Poprawka instalatora wymagająca zamknięcia Visual Studio instalacji w celu uniknięcia uszkodzonych instalacji.

- Naprawienie instalatora w celu zainstalowania zestawów odwoływnych aparatu Unity jako odpowiedniego składnika autonomicznego współużytkowania przez wszystkie wersje vstu.

- Naprawiono otwieranie skryptów za pomocą vstu w 64-bitowych wersjach aparatu Unity.

## <a name="1900"></a>1.9.0.0

Wydany 29 lipca 2014 r.

### <a name="new-features"></a>Nowe funkcje

- W oknie Dołączanie debugera aparatu Unity dodaj możliwość wprowadzania niestandardowego adresu IP i portu do debugowania.

- Dodaj opcję konfiguracji, aby ustawić unity do uruchamiania w tle.

- Dodaj opcję konfiguracji, aby wygenerować tylko pliki rozwiązania i projektu lub pliki projektu.

- Element docelowy uruchamiania: wybierz dołączenie do aparatu Unity lub dołącz do aparatu Unity i odtwarzania.

- Wyświetlanie tablic wielowymiarowych w debugerze.

- Obsługa nowych portów debugowania aplikacji Unity Player.

- Obsługa odwołań do nowych zestawów Unity, takich jak zestawy graficznego interfejsu użytkownika aparatu Unity 4.6.

- Dekonstrukcyjnie zamknięcia, aby prawidłowo wyświetlać zmienne lokalne podczas debugowania.

- Dekonstrukcja wygenerowanych iteratorów zmiennych na argumenty podczas debugowania.

- Zachowaj stan Eksploratora projektów aparatu Unity po ponownym załadowaniu projektu.

- Dodaj polecenie w celu zsynchronizowania eksploratora projektów aparatu Unity z bieżącym dokumentem.

### <a name="bug-fixes"></a>Poprawki błędów

- Napraw warunkowe punkty przerwania, których warunki są ustawione przed uruchomieniem debugera.

- Naprawiono odwołania do aparatu UnityEngine, aby uniknąć ostrzeżeń.

- Naprawienie analizowania wersji dla wersji beta aparatu Unity.

- Rozwiązano problem, który oznaczał, że zmienne nie były wyświetlane w oknie zmiennych lokalnych po trafieniu punktu przerwania lub krokowego.

- Napraw etykietki narzędzi zmiennych w Visual Studio 2013.

- Naprawiono generowanie dokumentacji funkcji IntelliSense dla aparatu Unity 4.5.

- Naprawienie komunikacji Unity/Visual Studio po ponownym załadowaniu domeny (odtwarzanie/zatrzymywanie w a unity).

- Naprawienie obsługi części Visual Studio motywów.

> [!IMPORTANT]
> Język C# jest dominującym językiem w ekosystemie aparatu Unity — nowe przykładowe zasoby znajdują się w języku C#, a dokumentacja aparatu Unity domyślnie ma wartość C# — usunęliśmy podstawową obsługę języków UnityScript i Boo, aby lepiej skupić się na środowiskach języka C#. W związku z tym rozwiązania VSTU są teraz tylko w języku C# i znacznie szybsze do załadowania.

## <a name="1820"></a>1.8.2.0

Wydany 7 stycznia 2014 r.

### <a name="new-features"></a>Nowe funkcje

- Pomiń problem w warstwie sieci aparatu obsługi skryptów aparatu Unity w uciecie Mavericks w celu zdalnego odnajdywania edytorów.

- Obsługa nowych portów w celu odnajdywania zdalnych odtwarzaczy Unity.

- Odwołanie do zestawu UnityEngine specyficznego dla bieżącego celu kompilacji.

- Dodaj ustawienie filtrowania plików, które mają być dołączane do wygenerowanych projektów.

- Dodaj ustawienie, aby wyłączyć wysyłanie dzienników konsoli do Visual Studio listy błędów. Jest to przydatne, jeśli używasz narzędzia PlayMaker lub konsoli Pro, ponieważ w a aparatu Unity może być zarejestrowane tylko jedno wywołanie zwrotne w celu odbierania dzienników konsoli.

- Dodaj ustawienie, aby wyłączyć generowanie symboli debugowania mdb. Jest to przydatne w przypadku generowania samodzielnie bazy danych mdb.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono regresję, gdy pliki otwierane w programie VS z poziomu aparatu Unity >= 4.2 utraciły intelliSense.

- Napraw nasze okna dialogowe programu VS w celu obsługi motywów niestandardowych.

- Naprawienie zamykania menu kontekstowego upe.

- Zapobiegaj awarii w a unity, gdy wygenerowany zestaw dla określonej wersji jest zsynchronizowany.

## <a name="1810"></a>1.8.1.0

Wydany 21 listopada 2013 r.

### <a name="new-features"></a>Nowe funkcje

- Dostosował kreatory MonoBehaviour za pomocą interfejsów API aparatu Unity 4.3.

- Kreatory MonoBehaviour filtrują interfejsy API aparatu Unity w zależności od wersji, z których korzystasz.

- Dodaj odwołanie do System.Xml. Linq to the projects for Unity > 4.1 (Linq to the projects for Unity > 4.1).

- Prettify nasze wywołania Debug.Log, aby nie uwzględniać początku stacktrace w komunikacie.

### <a name="bug-fixes"></a>Poprawki błędów

- Usunięto usterkę, która zakłócała domyślną obsługę plików JavaScript w Visual Studio.

- Naprawiono biały piksel wyświetlany w programie VS w tym czasie rzeczywistym.

- Naprawiono usunięcie zestawu UnityVS.VersionSpecific, jeśli jest on oznaczony jako tylko do odczytu przez scM.

- Naprawiono wyjątki podczas tworzenia gniazd w pakiecie UnityVS.

- Usunięto awarię w Visual Studio podczas ładowania obrazów trwałych z Visual Studio zestawów.

- Usunięto usterkę podczas generowania pliku UnityVS.VersionSpecific dla kompilacji źródłowych aparatu Unity.

- Naprawiono możliwe zablokowanie podczas otwierania gniazda w pakiecie aparatu Unity.

- Naprawiono obsługę projektu aparatu Unity z łącznikiem (-) w nazwie.

- Naprawiono otwieranie skryptów z aparatu Unity, aby nie mylić kolejności ALT+TAB dla aparatu Unity 4.2 i jego powyżej.

## <a name="1800"></a>1.8.0.0

Wydany 24 września 2013 r.

### <a name="new-features"></a>Nowe funkcje

- Znacząco zwiększono szybkość połączenia debugera.

- Automatyczna obsługa nawigacji do pliku i wiersza w aucie Unity 4.2 i jego systemach.

- Warunkowe punkty przerwania.

- Generator plików projektu obsługuje teraz szablony T4.

- Aktualizowanie kreatorów MonBehavior przy użyciu nowych interfejsów API.

- Dokumentacja funkcji IntelliSense w języku C# dla typów aparatu Unity.

- Ocena wyrażeń arytmetycznych i logicznych.

- Lepsze odnajdywanie edytorów zdalnych na potrzeby zdalnego debugowania w wersji zapoznawczej.

### <a name="bug-fixes"></a>Poprawki błędów

- Usunięto usterkę, która oznaczała wyciek wątku w programie VS po rozłączeniu debugera.

- Naprawiono biały piksel wyświetlany w programie VS.

- Naprawiono obsługę kliknięć na ikonie paska stanu.

- Naprawiono generowanie odwołań z zestawami w folderach wtyczek.

- Naprawiono tworzenie gniazd z pakietu UnityVS w przypadku wyjątków.

- Naprawiono wykrywanie nowych wersji aparatu UnityVS.

- Naprawiono monit menedżera licencji o wygaśnięciu licencji.

- Usunięto usterkę, która mogła spowodować, że lista procesów jest pusta w oknie dołączania debugera do procesu programu VS.

- Naprawiono zmianę wartości wartości boolean w widoku lokalnym.

## <a name="1220"></a>1.2.2.0

Wydany 9 lipca 2013 r.

### <a name="bug-fixes"></a>Poprawki błędów

- Obsługa w pełni kwalifikowanych nazw w ewaluatorze wyrażeń.

- Naprawiono blokowanie związane z obsługą wyjątków, gdy aparat skryptów aparatu Unity wysyła do nas nieprawidłowe dane ramki stosu.

- Naprawiono proces kompilacji dla obiektów docelowych sieci Web.

- Naprawiono błąd, który mógł wystąpić, Visual Studio został uruchomiony i że usunięty plik był na liście plików do otwarcia podczas uruchamiania.

- Naprawiono plik UnityVS.OpenFile w celu obsługi plików innych niż skrypty, takich jak skompilowane cieniowania.

- Teraz odwołujemy się do boo.lang i UnityScript.Lang ze wszystkich projektów języka C#.

- Naprawiono generowanie odwołań w projektach, jeśli projekt zawiera znaki specjalne.

- Obejście problemu z programem VS, który polegał na tym, że wywołania metod do usuniętych projektów wyzwalały wiele elementów MessageBox o wartości NullReferenceException.

- Naprawiono obsługę zestawów Unity 4.2 Beta.

## <a name="1210"></a>1.2.1.0

Wydany 9 kwietnia 2013 r.

### <a name="bug-fixes"></a>Poprawki błędów

- Rozwiązano problem z lokalnym wdrażaniem zestawów aparatu Unity w celu ukończenia kodu w przypadku wystąpienia błędu we/wy (na przykład plików tylko do odczytu lub plików zablokowanych przez Visual Studio).

- Naprawiono regresję, która oznaczała, że otwarcie skryptu z poziomu aparatu Unity nie skoncentrowałoby się na pliku, jeśli został on już otwarty w Visual Studio.

- Rozwiązano problem z wydajnością nowej obsługi wyjątków.

- Naprawiono powiązanie punktów przerwania w niektórych zewnętrznych plikach DLL.

## <a name="1200"></a>1.2.0.0

Wydana 25 marca 2013 r.

### <a name="new-features"></a>Nowe funkcje

- Znacząco zwiększono szybkość połączenia debugera.

- Zoptymalizowano Eksplorator projektów aparatu Unity dla większych projektów.

- Należy honorować Visual Studio, aby przerwać (lub nie) obsługę obsługiwanych i nieobsługiwanych wyjątków.

- Honoruj Visual Studio, aby wywołać toString dla zmiennych lokalnych.

- Dodaj nowe menu Debug -> Attach Unity debugger, którego można użyć do debugowania odtwarzaczy Unity.

- Zachowaj niestandardowe projekty dodane do rozwiązania UnityVS podczas generowania pliku rozwiązania.

- Dodaj nowy skrót klawiaturowy CTRL+ALT+M -> CTRL+H, aby wyświetlić dokumentację aparatu Unity dla funkcji lub członka aparatu Unity na pozycji karety.

- Weź pod uwagę pliki odpowiedzi kompilatora (rsp) podczas kompilowania z Visual Studio.

- Zdekonstruuj typy generowane przez kompilator, aby wyświetlać zmienne podczas debugowania metod generatora.

- Uproszczenie zdalnego debugowania przez usunięcie konieczności konfigurowania folderu udostępnionego w a aparatu Unity. Teraz wystarczy mieć dostęp do projektu aparatu Unity z systemu Windows.

- Zainstaluj niestandardowy profil aparatu Unity jako standardowy profil docelowy .NET. Rozwiązuje to wszystkie wyniki fałszywie dodatnie, które może pokazać reSharper.

- Omiń usterkę aparatu skryptów aparatu Unity, aby debuger nie przerwał działania w nierejestrowanych wątkach.

- Przepracuj program otwierający pliki, aby uniknąć sytuacji wyścigu w programie VS, w którym twierdzi, że może otwierać pliki, podczas awarii w otwartym żądaniu pliku.

- Aparat UnityVS prosi teraz o odświeżenie kompilacji podczas kompilowania projektu przez program VS, a nie podczas zapisywania pliku.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono nasz niestandardowy profil .NET

- Rozwiązano problem z integracją motywów, co rozwiązało nasze problemy z ciemnym motywem programu VS 2012.

- Naprawiono skrót do szybkiego zachowania w programie VS 2012.

- Rozwiązano problem krokowy, który mógł wystąpić, gdy debugowanie i wątek inny niż główny trafiał punkt przerwania.

- Naprawiono uzupełnianie aliasów typów, takich jak int, w języku UnityScript i boo.

- Usunięto wyjątek podczas pisania nowego ciągu UnityScript lub Boo.

- Naprawiono wyjątki w menu aparatu Unity, gdy rozwiązanie nie zostało załadowane.

- Usunięto usterkę FUNKCJIS-48: wpisanie podwójnego cudzysłowu czasami powodować błąd i przerwać całą funkcję (uzupełnianie kodu, wyróżnianie składni itp.).

- Usunięto usterkę WS-46: Zduplikowany otwarty plik skryptu (UnityScript) po kliknięciu listy błędów Visual Studio.

- Usunięto usterkę , która oznaczała, że logo łączności UNITY na pasku stanu nie obsługuje zdarzeń myszy w programie VS 2012.

- Usunięto usterkę w narzędziu LAMPS-44: klawisze CTRL+SHIFT+Q nie są dostępne w programie VS 2012 w przypadku szybkich monobehaviours.

- Usunięto usterkę Wsad-40: Wybrane elementy w Eksploratorze projektów aparatu Unity są nieczytelne, gdy okno jest nieaktywne w motywie "ciemnym" programu VS2012.

- Usunięto usterkę w numerze LAMPS-39: Problem z tokenizami ciągów o zmiękchu ucieczki.

- Usunięto usterkę w funkcji LAMPS-35: Wywołaj toString na obiektach podczas inspekcji zmiennych.

- Usunięto usterkę SYSTEMU LAMPS-27: Niespójność okna symbolu Goto z motywem "ciemnym" w programie VS2012.

- Usunięto usterkę NAPRAWIONOS-11: Locals in coroutines (Lokalne w coroutinesach).

## <a name="1100---beta-release"></a>1.1.0.0 — wersja beta
Wydana 9 marca 2013 r.

## <a name="10130"></a>1.0.13.0
Wydany 21 stycznia 2013 r.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono blokadę Visual Studio, która mogła wystąpić, jeśli debuger docelowy wysyła zdarzenia nieprawidłowych wątków. Zwykle dzieje się tak podczas debugowania zdalnego aparatu Unity w programie OSX.

- Naprawiono Visual Studio, która mogła wystąpić, jeśli wyjątek wyłączy debuger.

- Naprawiono nasze pomocniki MonoBehavior, gdy monoBehavior języka C# znajduje się w przestrzeni nazw.

- Naprawiono etykietki narzędzi debugera dla języka UnityScript w Visual Studio 2012 r.

- Naprawiono generowanie projektu, gdy tylko stałe debugowania są zmieniane z aparatu Unity.

- Naprawiono nawigację za pomocą klawiatury w eksploratorze projektów aparatu Unity.

- Naprawiono kolorowanie kodu UnityScript dla ciągów ze znakami ucieczki.

- Naprawiono nasz otwieracz plików, aby odgadnąć lepszą nazwę projektu, gdy jest używana poza unity. Jest to konieczne, gdy użytkownik korzysta z otwieracza plików trzeciej części w a aparatu Unity, który deleguje do aparatu UnityVS.

- Naprawiono obsługę długich komunikatów wysyłanych z aparatu Unity do unityVS. Wcześniej długie komunikaty mogły ulegać awarii naszej części obsługi komunikatów w unityVS. W związku z tym czasami aparat UnityVS nie otwiera pliku z aparatu Unity.

## <a name="10120"></a>1.0.12.0
Wydany 3 stycznia 2013 r.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono Visual Studio blokady, która mogła wystąpić Visual Studio, gdy Visual Studio punkt przerwania.

- Usunięto usterkę, która oznaczała, że niektóre punkty przerwania nie były trafione po ponownej kompilacji skryptów gry aparatu Unity.

- Naprawiono debuger w celu poprawnego powiadamiania Visual Studio, gdy punkty przerwania były niepowiązane.

- Rozwiązano problem z rejestracją, który mógł uniemożliwiać debugerowi Visual Studio debugowanie programów natywnych.

- Naprawiono wyjątek, który mógł wystąpić podczas oceny wyrażeń UnityScript i Boo.

- Naprawiono regresję, w przypadku której zmiana poziomu interfejsu API platformy .NET w a aparatu Unity nie wyzwalała aktualizacji plików projektu.

- Usunięto usterkę interfejsu API, w przypadku której kod użytkownika nie mógł uczestniczyć w obsłudze wywołania zwrotnego dziennika.

## <a name="10110"></a>1.0.11.0
Wydany 28 listopada 2012 r.

### <a name="new-features"></a>Nowe funkcje

- Oficjalne wsparcie aparatu Unity 4.

- Manipulowanie skryptami w eksploratorze projektów aparatu Unity.

- Integracja w Visual Studio przejdź do okna Przejdź do.

- Analizowanie komunikatu konsoli informacji, aby kliknięcie na liście błędów przekierowyło Cię do pierwszej ramki stosu z symbolami.

- Dodaj interfejs API, aby pozwolić użytkownikowi na uczestnictwo w generowaniu projektu.

- Dodaj interfejs API, aby pozwolić użytkownikowi na uczestnictwo w logcallback.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono regresję w tle eksploratora projektów aparatu Unity w Visual Studio 2012 r.

- Naprawiono generowanie projektu dla użytkowników pełnego profilu .NET.

- Naprawiono generowanie projektu dla użytkowników obiektu docelowego sieci Web.

- Naprawiono generowanie projektu w celu dołączania symboli kompilacji DEBUG i TRACE, tak jak w przypadku aparatu Unity.

- Usunięto awarię podczas używania znaków specjalnych w oknie symbolu Goto.

- Usunięto awarię, jeśli nie można wstrzyknąć naszej ikony Visual Studio pasku stanu aplikacji.

## <a name="10100"></a>1.0.10.0
Wydany 9 października 2012 r.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono tło eksploratora projektów aparatu Unity w programie Visual Studio 2010.

- Naprawiono błąd Visual Studio, który mógł wystąpić, jeśli aparat UnityVS próbował dołączyć debuger do aparatu Unity, którego interfejs debugera wcześniej ulegał awarii.

- Rozwiązano problem Visual Studio, który mógł wystąpić w przypadku ustawienia punktu przerwania i ponownego załadowania domeny aplikacji.

- Naprawiono sposób pobierania zestawów z aparatu Unity, aby uniknąć blokowania plików i mylić proces kompilacji aparatu Unity.

## <a name="1090"></a>1.0.9.0

Wydany 3 października 2012 r.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono generowanie projektu, gdy projekt aparatu Unity zawiera rzeczywiste zasoby Języka JavaScript.

- Naprawiono obsługę błędów podczas oceny wyrażeń.

- Naprawiono ustawienie nowych wartości na pola typów wartości.

- Naprawiono możliwe efekty uboczne podczas najechania kursorem na wyrażenia z edytora kodu.

- Naprawiono sposób wyszukiwania typów w załadowanych zestawach w celu oceny wyrażeń.

- Usunięto usterkę NRS-21: Ocena przypisania dla obiektów unity nie ma wpływu.

- Usunięto usterkę SYSTEMU UNITYS-21: Nieprawidłowy wskaźnik podczas oceny wywołania metody do interfejsu API obliczeń matematycznych aparatu Unity.

## <a name="1080"></a>1.0.8.0

Wydana 26 września 2012 r.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiliśmy sposób, w jaki nasz otwieracz skryptów pozyskał ścieżkę do projektu, aby upewnić się, że jest w stanie otworzyć zarówno skrypty Visual Studio, jak i skrypty.

- Usunięto usterkę z punktami przerwania utworzonymi podczas uruchamiania sesji debugowania, która Visual Studio się zablokować.

- Naprawiono sposób rejestrowania unityVS w Visual Studio 2010 r.

## <a name="1070"></a>1.0.7.0

Wydana 14 września 2012 r.

### <a name="new-features"></a>Nowe funkcje

- Visual Studio 2012.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono generowanie plików projektu edytora i wtyczek w celu dopasowania ich do zachowania aparatu Unity.

- Naprawiono tłumaczenie symboli .pdb na platformie Unity 4.

> [!IMPORTANT]
> Ze względu na Visual Studio 2012 roku musieliśmy zmienić nazwę kilku plików i przenieść kilka innych. Pakiet UnityVS do importowania aparatu Unity ma teraz nazwę UnityVS 2010 lub UnityVS 2012, odpowiednio Visual Studio 2010 i Visual Studio 2012. Ta wersja wymaga również ponownego wygenerowania plików projektu UnityVS.

## <a name="1060---internal-build"></a>1.0.6.0 — kompilacja wewnętrzna
Wydana 12 września 2012 r.

## <a name="1050"></a>1.0.5.0

Wydana 10 września 2012 r.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono generowanie plików projektu, gdy skrypty lub cieniowania miały nieprawidłowy znak XML.

- Naprawiono wykrywanie wystąpień aparatu Unity, gdy unity było połączone z serwerem zasobów. Wyzwoliło to błędy otwierania plików z aparatu Unity i automatyczne połączenie Visual Studio debugera.

## <a name="1040"></a>1.0.4.0

Wydana 5 września 2012 r.

### <a name="new-features"></a>Nowe funkcje

- Automatyczna konwersja symboli debugowania w a unity.

    Jeśli masz zestaw .NET .dll ze skojarzonym plikiem .pdb w folderze Asset, po prostu ponownie zaimportuj zestaw, a unityVS przekonwertuje plik .pdb na plik symboli debugowania, który będzie zrozumiały dla aparatu skryptów aparatu Unity, i będzie można wchodzić do zestawów .NET z poziomu aparatu UnityVS.

### <a name="bug-fixes"></a>Poprawki błędów

- Usunięto awarię aparatu UnityVS podczas debugowania spowodowaną przez wyjątki zgłaszane przez metody lub właściwości w a aparatu Unity.

## <a name="1030"></a>1.0.3.0

Wydana 4 września 2012 r.

### <a name="new-features"></a>Nowe funkcje

- Nowa opcja konfiguracji, która wyłącza użycie aparatu UnityVS do otwierania plików z aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono generowanie odwołań do aparatu UnityEditor dla projektów innych niż edytor.

- Naprawiono definicję symbolu UNITY_EDITOR dla projektów nieedytacyjnych.

- Usunięto losową awarię programu VS spowodowaną przez niestandardowy pasek stanu.

## <a name="1020"></a>1.0.2.0

Wydana 30 sierpnia 2012 r.

### <a name="bug-fixes"></a>Poprawki błędów

- Rozwiązano konflikt z debugerem PythonTools.

- Naprawiono odwołania do mono.Ichil.

- Usunięto usterkę w skrypcie pobierania zestawów skryptów z aparatu Unity za pomocą aparatu Unity 4 b7.

## <a name="1010"></a>1.0.1.0

Wydana 28 sierpnia 2012 r.

### <a name="new-features"></a>Nowe funkcje

- Obsługa wersji zapoznawczej aparatu Unity 4.0 Beta.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono inspekcję właściwości zgłaszających wyjątki.

- Naprawiono malejąco do obiektów podstawowych podczas inspekcji obiektów.

- Naprawiono pustą listę rozwijaną dla punktu wstawiania w kreatorze MonoBehavior.

- Poprawiono uzupełnianie bibliotek dll w folderze Asset dla unityScript i Boo.

## <a name="1000---initial-release"></a>1.0.0.0 — wersja początkowa
Wydana 22 sierpnia 2012 r.
