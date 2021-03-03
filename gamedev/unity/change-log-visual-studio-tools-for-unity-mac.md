---
title: Dziennik zmian (Visual Studio Tools for Unity, Mac) | Microsoft Docs
description: Wyświetl dziennik zmian dla Visual Studio Tools for Unity i Mac. Zobacz zmiany w wersji 1.0.0.0 przez 2.7.0.0 i poza nią.
ms.custom: ''
ms.date: 3/1/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: f11c5c1407d16d7a82a9d8d24e6a8dd3a04e57eb
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683378"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Dziennik zmian (narzędzia Visual Studio Tools for Unity, komputery Mac)

Visual Studio Tools for Unity dziennik zmian.

## <a name="2920"></a>2.9.2.0
Wydana 2 marca 2021

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stałe wyróżnianie wyszukiwania w oknie dialogowym komunikatu środowiska Unity.

  - Rozwiązano problemy ze stabilnością w widoku TreeView projektu środowiska Unity.

- **Debugera**

  - Stała obsługa warunkowych punktów przerwania.

## <a name="2910"></a>2.9.1.0
Wydanie 9 lutego 2021

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę uruchamiania i debugowania testów aparatu Unity z poziomu środowiska IDE

- **Sprawozdanie**

  - Dodano `Active Scene` do elementów lokalnych, pokazując obiekty głównej gry.

  - Dodano `this.gameObject` do elementów lokalnych, o ile jest szeroko używany w projektach Unity.

  - Dodano `Children` `Components` grupy i do wszystkich `GameObject` wystąpień, dzięki czemu można łatwo wyświetlić wszystkie hierarchie obiektów.

  - Dodano `Scene Path` do wszystkich `GameObject` wystąpień, aby pokazać lokalizację w scenie.

  - Dodano obsługę `JobEntityBatch` /lambdas w przypadku używania jednostek z generatorami źródeł.

  - Ulepszona obsługa wyświetlania dużych tablic (przy użyciu funkcji zasobnika indeksów).

  - Dodano brakujące komunikaty aparatu Unity dla interfejsu API 2019,4.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Rozwiązano problemy ze stabilnością w oknie dialogowym komunikatu aparatu Unity

  - Rozwiązano różne problemy z interfejsem użytkownika dla języków innych niż plk.

  - Rozwiązano problemy ze stabilnością dotyczące [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) diagnostyki.

- **Debugera**

  - Rozwiązano problemy z rozłączeniem maszyny wirtualnej podczas korzystania z `Trace` metod.

- **Sprawozdanie**

  - Stałe filtrowanie przestarzałych właściwości zgłaszających wyjątki.

## <a name="2900"></a>2.9.0.0
Wydana 20 stycznia 2021

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę `raytrace shaders` `UXML` `USS` plików i.

  - Zaktualizowano interfejs API komunikatów Unity (dla wszystkich metod używanych jako współprocedury).

  - Zaktualizowano wykrywanie Android SDK.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) Diagnostyka, dająca błędne ostrzeżenia dotyczące procedur współdziałania i `AssetPostprocessor.OnAssignMaterialModel` .

## <a name="2840"></a>2.8.4.0
Wydanie 15 grudnia 2020

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Rozwiązano problem związany z niezawodnością podczas zamykania kreatora tworzenia zdarzeń aparatu Unity.

## <a name="2830"></a>2.8.3.0
Wydana 10 listopada 2020

### <a name="bug-fixes"></a>Poprawki błędów

- **Oknie**

  - Naprawiono dołączenie do aparatu Unity nawet wtedy, gdy w rozwiązaniu nie ma projektu rozszerzenia VSTU.

## <a name="2820"></a>2.8.2.0
Wydana 27 października 2020

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Ulepszona [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md) Diagnostyka do zastosowania do wszystkiego dziedziczonego z `Component` , a nie tylko `MonoBehaviour` .

## <a name="2810"></a>2.8.1.0
Wydanie 13 października 2020

### <a name="new-features"></a>Nowe funkcje

- **Sprawozdanie**

  - Dodano obsługę niejawnej konwersji z wywołaniami. Wcześniej ewaluatora wymusza dokładne sprawdzanie typów, co powoduje wyświetlenie `Failed to find a match for method([parameters...])` komunikatów ostrzegawczych.

- **Integration**

  - Dodano [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) diagnostykę. Nie należy używać `System.Reflection` funkcji w przypadku komunikatów o znaczeniu krytycznym, takich jak `Update` ,, `FixedUpdate` `LateUpdate` , lub `OnGUI` .

  - Ulepszone [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) i [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) uniemożliwione, z obsługą wszystkich `AssetPostprocessor` metod statycznych.

  - Dodano [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md) pominięcie dla elementu `CS8618` . `C# 8.0` wprowadza typy odwołań do wartości null i niedopuszczające wartości null. Wykrywanie inicjalizacji typów dziedziczących z `UnityEngine.Object` nie jest obsługiwane i spowoduje błędy.

  - Teraz korzystamy z tego samego odtwarzacza i mechanizmu generowania projektu asmdef dla obu systemów Unity 2019. x i 2020. x +.
  
  - Ulepszone środowisko użytkownika podczas generowania komunikatów aparatu Unity za pomocą kreatora.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono nieoczekiwane uzupełnienie komunikatów w komentarzach.

## <a name="2800"></a>2.8.0.0 
Wydanie 14 września 2020

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała generacja projektu odtwarzacza z użyciem aparatu Unity. x.

## <a name="2710"></a>2.7.1.0
Wydana 5 sierpnia 2020

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Zaktualizowano interfejs API komunikatów aparatu Unity do 2019,4.

  - Dodano [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) pominięcie dla elementu `CA1823` . Pola prywatne z `SerializeField` `SerializeReference` atrybutami lub nie powinny być oznaczone jako nieużywane (FxCop).
  
  - Dodano [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) pominięcie dla elementu `CA1822` . Komunikaty aparatu Unity nie powinny być oflagowane jako kandydaci dla `static` modyfikatora (FxCop).

  - Dodano [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) pominięcie dla elementu `CA1801` . Nie należy usuwać nieużywanych parametrów z komunikatów Unity (FxCop).
  
  - Dodano `MenuItem` obsługę do funkcji [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) pomijania.  

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawione [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) i [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) pomijające nie działają z dodatkowymi nawiasami ani z argumentami metod.
  
  - Naprawione obowiązkowe odświeżenie bazy danych zasobów, nawet jeśli funkcja AutoRefresh została wyłączona w ustawieniach aparatu Unity.

## <a name="2700"></a>2.7.0.0
Wydanie 23 czerwca 2020

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę utrwalania folderów rozwiązań, gdy aparat Unity ponownie generuje rozwiązanie i projekty.

  - Dodano [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) diagnostykę. Wykryj niepoprawną sygnaturę metody z `InitializeOnLoadMethod` `RuntimeInitializeOnLoadMethod` atrybutem or.

  - Dodano [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) diagnostykę. Użycie `Invoke` , `InvokeRepeating` , `StartCoroutine` lub `StopCoroutine` z pierwszym argumentem będącym literałem ciągu nie jest bezpieczne.

  - Dodano [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) diagnostykę. `SetPixels` wywołanie jest powolne.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oknie**

  - Naprawiono Tworzenie punktów przerwania, gdy gra jest uruchomiona w starym środowisku uruchomieniowym mono (próba powiązania punktu przerwania zaraz po jego utworzeniu). 
  
- **Integration**

  - Nie należy resetować zaznaczenia podczas filtrowania komunikatów w Kreatorze komunikatów aparatu Unity.
  
  - Stałe [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) i [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) pomijane z następującymi regułami: pomijanie `IDE0044` (tylko do odczytu), `IDE0051` (nieużywane), `CS0649` (nigdy nie są przypisywane) dla wszystkich pól, które mają atrybut SerializeField. Pomijaj element `CS0649` (nigdy nieprzypisane) dla pól publicznych wszystkich typów rozszerzających elementy `Unity.Object`.

  - Stałe sprawdzanie parametrów typu ogólnego [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) .

- **Sprawozdanie**

  - Stałe porównanie równości z wyliczeniem.

## <a name="2610"></a>2.6.1.0
Wydana 19 maja 2020

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Ostrzegaj, jeśli nie można utworzyć serwera obsługi komunikatów na stronie aparatu Unity.

  - Prawidłowo uruchamiaj analizatory podczas kompilacji uproszczonej.

  - Stała dokumentacja interfejsu API z instalacjami koncentratora Unity.
  
  - Stały wizualizator debugera.

## <a name="2600"></a>2.6.0.0
Opublikowano 14 kwietnia 2020

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) diagnostykę. Wykrywaj i Zawijaj wywołania procedur wspólnych w programie `StartCoroutine()` .

  - Dodano [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) diagnostykę. Wykryj i usuń nieprawidłowy lub nadmiarowy `SerializeField` atrybut.

  - Dodano [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) diagnostykę. Wykryto `GetComponent()` wywołanie z typem niebędącym składnikiem lub bez interfejsu.

  - Dodano [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) pominięcie dla elementu `IDE0051` . Nie należy flagować metod przy użyciu `ContextMenu` atrybutu lub odwołania do pola z `ContextMenuItem` atrybutem jako nieużywane.

  - Dodano [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) pominięcie dla elementu `IDE0051` . Nie należy oznaczać pól `ContextMenuItem` atrybutem jako nieużywane.

  - Dodano [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) pominięcie dla elementu `IDE0044` . Nie należy tworzyć pól z `ContextMenuItem` atrybutem tylko do odczytu.

  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md)[`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md)i [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) teraz działa dla obu `SerializeReference` `SerializeField` atrybutów.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Wysyłaj polecenia uruchamiania/zatrzymywania tylko do aparatu Unity, gdy Edytor jest w stanie komunikować się.

  - Stała dokumentacja sekcji szybkich informacji z dziedziczonymi komunikatami.

  - Stały zakres komunikatów dla `CreateInspectorGUI` wiadomości.

  - Nie należy raportować [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) metod z modyfikatorami polimorficznymi.

- **Sprawozdanie**

  - Stała obsługa aliasów użycia.
  
  - Stała obsługa wartości null.  

## <a name="2520"></a>2.5.2.0

Wydana 23 marca, 2020

### <a name="bug-fixes"></a>Poprawki błędów

- **Oknie**

  - Naprawiono rejestrację wątków po dołączeniu.

## <a name="2510"></a>2.5.1.0

Wydana 3 marca 2020

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) pominięcie dla elementu `IDE0051` . Metody prywatne używane z metodami Invoke, InvokeRepeating, StartCoroutine lub StopCoroutine nie powinny być oznaczone jako nieużywane.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała dokumentacja OnDrawGizmos/OnDrawGizmosSelected.

- **Sprawozdanie**

  - Stała Inspekcja argumentu lambda.

## <a name="2501"></a>2.5.0.1

Wydana 19 lutego 2020

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) sprawdzenie diagnostyki dla nieprawidłowej sygnatury wiadomości. Podczas sprawdzania typów z wieloma poziomami dziedziczenia ta Diagnostyka może zakończyć się niepowodzeniem z następującym komunikatem: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="2500"></a>2.5.0.0

Wydana 22 stycznia 2020

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę plików HLSL.
  
  - Przełączono do nowego interfejsu użytkownika okna dialogowego.
  
  - Przełączono do nowej dostępnej siatki właściwości dla ustawień.

  - Dodano [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) pominięcie dla elementu `IDE0051` . Pola prywatne z `SerializeField` atrybutem nie powinny być oznaczone jako nieużywane.

  - Dodano [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) pominięcie dla elementu `CS0649` . Pola z `SerializeField` atrybutem nie powinny być oznaczone jako nieprzypisane.  

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała generacja projektu ( `GenerateTargetFrameworkMonikerAttribute` element docelowy nie zawsze znajdował się poprawnie).

- **Sprawozdanie**

  - Stałe obliczanie ciągu (nieużywające wywołań ToString ())

## <a name="2420"></a>2.4.2.0

Wydanie 3 grudnia 2019

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała Diagnostyka ze zdefiniowanymi przez użytkownika interfejsami.

  - Stałe szybkie etykietki narzędzi z nieprawidłowo sformułowanymi wyrażeniami.
  
## <a name="2410"></a>2.4.1.0

Wydana 6 listopada, 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę procesów w tle środowiska Unity. (Debuger może połączyć się z głównym procesem zamiast procesu podrzędnego).

  - Dodano szybką etykietkę narzędzia dla komunikatów aparatu Unity wyświetlającą skojarzoną dokumentację.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono analizatora porównywania tagów `UNT0002` za pomocą zaawansowanych wyrażeń binarnych i wywołań.

### <a name="deprecated-features"></a>Przestarzałe funkcje

- **Integration**

  - W przyszłości program Visual Studio Tools for Unity obsługuje tylko program Visual Studio 2017 +.

## <a name="2400"></a>2.4.0.0

Wydanie 15 października 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) pominięcie dla `IDE0060` (nieużywany parametr) dla wszystkich komunikatów aparatu Unity.

  - Dodano szybką etykietkę narzędzia dla pól otagowanych za pomocą `TooltipAttribute` . (Ta wartość będzie działała w przypadku prostej metody dostępu get używającej również tego pola).

## <a name="2330"></a>2.3.3.0

Wydanie 23 września, 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano nowy element do pomijania dla IDE0060, aby zapobiec wyświetlaniu przez środowisko IDE szybkiej naprawy w celu usunięcia nieużywanych parametrów.
    - `USP0005` dla `IDE0060` : komunikaty aparatu Unity są wywoływane przez środowisko uruchomieniowe aparatu Unity.

## <a name="2320"></a>2.3.2.0

Wydanie 16 września 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Wyjaśniono, że program Visual Studio obsługuje projekty Unity przez dodanie nowej diagnostyki specyficznej dla aparatu Unity. Wprowadziliśmy również zmiany powodujące, że środowisko IDE działa teraz bardziej inteligentnie dzięki pomijaniu ogólnej diagnostyki języka C#, która nie dotyczy projektów Unity. Na przykład IDE nie będzie wyświetlał szybkiej poprawki, aby zmienić zmienną inspektora, do `readonly` której nie można zmodyfikować zmiennej w edytorze aparatu Unity.
    - `UNT0001`: Komunikaty aparatu Unity są wywoływane przez środowisko uruchomieniowe, nawet jeśli są puste, nie deklaruj ich, aby uniknąć przetwarzania uncesseray przez środowisko uruchomieniowe aparatu Unity.
    - `UNT0002`: Porównanie tagów przy użyciu równości ciągów jest wolniejsze niż wbudowana Metoda CompareTag.
    - `UNT0003`: Użycie ogólnego formularza GetComponent jest preferowane dla bezpieczeństwa typu.
    - `UNT0004`: Komunikat aktualizacji jest zależny od szybkości ramki i powinien używać czasu deltaTime zamiast czasu. fixedDeltaTime.
    - `UNT0005`: Komunikat FixedUpdate jest niezależny od szybkości klatek i powinien używać Time. fixedDeltaTime zamiast Time. deltaTime.
    - `UNT0006`: Wykryto niepoprawną sygnaturę metody dla tego komunikatu aparatu Unity.
    - `UNT0007`: Unity zastępuje operator porównania null dla obiektów Unity, które są niezgodne z łączeniem zerowym.
    - `UNT0008`: Unity zastępuje operator porównania null dla obiektów Unity, które są niezgodne z propagacją wartości null.
    - `UNT0009`: W przypadku zastosowania atrybutu InitializeOnLoad do klasy należy dostarczyć statyczny Konstruktor. Atrybut InitializeOnLoad zapewnia, że zostanie on wywołany podczas uruchamiania edytora.
    - `UNT0010`: Działania bezdziałające powinny być tworzone tylko przy użyciu AddComponent (). MonoBehaviour to składnik, który musi zostać dołączony do obiektu GameObject.
    - `UNT0011`: ScriptableObject powinien być utworzony tylko przy użyciu metody CreateInstance (). Obiekt ScriptableObject musi zostać utworzony przez aparat Unity do obsługi metod komunikatów aparatu Unity.
    - `USP0001` dla `IDE0029` : obiekty Unity nie powinny używać łączenia zerowego.
    - `USP0002` dla `IDE0031` : obiekty Unity nie powinny używać propagacji o wartości null.
    - `USP0003` dla `IDE0051` : komunikaty aparatu Unity są wywoływane przez środowisko uruchomieniowe aparatu Unity.
    - `USP0004` dla `IDE0044` : pola z atrybutem SerializeField nie powinny być tylko do odczytu.

## <a name="2310"></a>2.3.1.0

Wydanie 4 września 2019

### <a name="new-features"></a>Nowe funkcje

- **Sprawozdanie**

  - Dodano obsługę wyświetlania lepszych typów, tj. `List<object>` zamiast `List'1[[System.Object, <corlib...>]]` .

  - Dodano obsługę dostępu do elementu członkowskiego wskaźnika, `p->data->member` tj.

  - Dodano obsługę niejawnych konwersji w inicjatorach tablicy, tj `new byte [] {1,2,3,4}` .

  - Dodano obsługę edytora szesnastkowego podczas sprawdzania tablic bajtowych i ciągów.

## <a name="2300"></a>2.3.0.0

Opublikowano 13 sierpnia 2019

### <a name="bug-fixes"></a>Poprawki błędów

- **Sprawozdanie**

  - Rozwiązywanie problemów z wyjątkami.

  - Stała Ocena identyfikatorów pseudo (takich jak $exception).

  - Zapobiegaj awarii podczas usuwania odwołań do nieprawidłowych adresów.  

  - Rozwiązano problem z niezaładowanymi domenami aplikacji.

## <a name="2200"></a>2.2.0.0

Wydana 25 lipca 2019

### <a name="bug-fixes"></a>Poprawki błędów

- **Sprawozdanie**

  - Stała Inspekcja przy użyciu typów IntPtr.

- **Oknie**

  - Stała obsługa catchpoints i punktów przerwania funkcji.

## <a name="2130"></a>2.1.3.0

Wydanie 9 lipca 2019

### <a name="new-features"></a>Nowe funkcje

- **Oknie**

  - Dodano obsługę przechwytywania podklas wyjątków.

  - Dodano obsługę protokołu MDS 2,51.

- **Integration**

  - Dodano obsługę plików asmdef.

  - Przełącz do trybu zmiany nazwy, gdy plik zostanie dodany z szablonu (aby naśladować zachowanie edytora Unity).

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała obsługa nieprawidłowych komunikatów podczas komunikowania się z graczami aparatu Unity.

- **Sprawozdanie**

  - Stała obsługa przestrzeni nazw w wyrażeniach.

## <a name="2120"></a>2.1.2.0

Wydanie 2 lipca 2019

### <a name="bug-fixes"></a>Poprawki błędów

- **Sprawozdanie**

  - Naprawiono raportowanie błędów z wyrażeniami niemożliwymi do przeanalizowania.

## <a name="2110"></a>2.1.1.0

Wydana 27 czerwca 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Zaktualizowano interfejs API o bezzachowań do 2019,1.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała wydajność Eksploratora projektów środowiska Unity.

  - Naprawiono ostrzeżenia i błędy raportowane w przypadku włączenia uproszczonej kompilacji.

  - Stała wydajność lekkiej kompilacji.

## <a name="2100"></a>2.1.0.0

Wydana 20 czerwca 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Wyłączono pełną kompilację dla projektów środowiska Unity, na korzyść używania błędów i ostrzeżeń funkcji IntelliSense. Istotny aparat Unity tworzy rozwiązanie programu Visual Studio z projektami biblioteki klas, które reprezentują, co Unity działa wewnętrznie. Z tego powodu wynik kompilacji w programie Visual Studio nigdy nie jest używany lub nie jest wybierany przez środowisko Unity, ponieważ ich potok kompilacji jest zamknięty. Kompilowanie w programie Visual Studio jest samo zużywanie zasobów. Jeśli potrzebujesz pełnej kompilacji, ponieważ masz narzędzia lub Instalatora, które od niego zależą, możesz wyłączyć tę optymalizację (ustawienia/narzędzia dla aparatu Unity/wyłączyć pełną kompilację projektów).
  
  - Dodano obsługę pakietów Unity w UPE. Widoczne są tylko pakiety, do których istnieją odwołania (przy użyciu manifest.jsw `Packages` folderze) i pakiety lokalne (osadzone w `Packages` folderze).

## <a name="2021"></a>2.0.2.1

Wydana 30 maja 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano niestandardową ikonę dla celów wykonywania środowiska Unity.

## <a name="2020"></a>2.0.2.0

Wydanie 2 kwietnia 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę automatycznego odświeżania bazy danych zasobów aparatu Unity przy zapisywaniu. Ta funkcja jest domyślnie włączona i wyzwala ponowną kompilację po stronie aparatu Unity podczas zapisywania skryptu w programie Visual Studio. Tę funkcję można wyłączyć w programie Tools\Options\Tools for Unity\Refresh Unity AssetDatabase przy zapisywaniu.

  - Dodano obsługę ustawiania preferowanej instalacji aparatu Unity dla dokumentacji w trybie offline.

  - Dodano menu kontekstowe dla nowego edytora.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oknie**

  - Stałe filtrowanie zestawów i inspekcja ramek z pustymi ramkami.

## <a name="2011"></a>2.0.1.1
 
 Wydana 26 marca 2019

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Tymczasowo Ustaw mono jako domyślny i możliwy do użycia debuger dla tej bardzo konkretnej wersji.

## <a name="2006"></a>2.0.0.6

Wydana 26 marca 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę funkcji "Dołącz do środowiska Unity i Play".

## <a name="2005"></a>2.0.0.5

Wydana 20 marca 2019

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Zachowaj właściwości zewnętrzne podczas przetwarzania pliku rozwiązania.
  
- **Sprawozdanie**

  - Dodano obsługę nazw kwalifikowanych aliasem (tylko globalna przestrzeń nazw dla teraz). Dlatego ewaluatora wyrażeń akceptuje teraz typy przy użyciu formularza Global:: Namespace. Type.

  - Dodano obsługę `pointer[index]` formularza, która jest semantycznie identyczna z formularzem dereferencji wskaźnika `*(pointer+index)` .

## <a name="2004"></a>2.0.0.4

Wydana 5 marca 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Zaktualizowano `ScriptableObject` interfejs API.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Usunięto przestrzenie nazw z szablonów.

## <a name="2003"></a>2.0.0.3
 
 Wydana 5 marca 2019

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Pola publiczne i serializowane nie będą już powodowały ostrzeżeń. `CS0649` `IDE0051` W projektach Unity, które utworzyły te komunikaty, zostały pominięte ostrzeżenia kompilatora.

- **Integration**

  - Monituj o dołączenie do określonego wystąpienia, jeśli więcej niż jeden proces Unity jest uruchomiony.

- **Sprawozdanie**

  - Dodano obsługę funkcji lokalnych.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oknie**

  - Stały odczyt atrybutu niestandardowego dla nazwanych argumentów w przypadku używania starych wersji protokołu.

## <a name="2002"></a>2.0.0.2

Wydana 4 lutego 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Zaktualizowano interfejs API z zachowaniem.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oknie**

  - Naprawiono wartości pierwotne w debugerze.

## <a name="2001"></a>2.0.0.1

Wydanie 4 grudnia 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stałe zawiera samodzielne pakiety instalacji.

## <a name="2000"></a>2.0.0.0
 Wydanie 4 grudnia 2018

### <a name="new-features"></a>Nowe funkcje

- **Oknie**

  - Zamieniono debuger Unity na komputerze Mac z tym samym debugerem podstawowego aparatu Unity z systemu Windows.

  - Zamieniono NRefactory na korzyść Roslyn na potrzeby oceny wyrażenia.

  - Dodano obsługę wskaźników: dereferencja, rzutowania lub arytmetycznego wskaźnika (w tym celu wymagane są zarówno środowisko Unity 2018.2 + i nowe środowisko uruchomieniowe).

  - Dodano obsługę widoku wskaźnika tablicy (na przykład w języku C++). Wypełnij wyrażenie wskaźnika, a następnie Dołącz przecinek i liczbę elementów, które chcesz zobaczyć.

  - Dodano obsługę konstrukcji asynchronicznych.

  - Dodano obsługę pseudo zmiennych (wyjątków i identyfikatorów obiektów).

### <a name="bug-fixes"></a>Poprawki błędów

- **Oknie**

  - Obliczanie stałych wyrażeń z nieprawidłowo sformułowanymi lub nieobsługiwanymi wyrażeniami.

## <a name="1700"></a>1.7.0.0

Wydana 13 listopada 2018

### <a name="new-features"></a>Nowe funkcje

- **Oknie**

  - Dodano więcej informacji o kliencie (adres IP, Nazwa maszyny) w oknie dialogowym dołączania.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oknie**

  - Naprawiono zakleszczenie w bibliotece używanej do komunikacji z aparatem debugera aparatu Unity, co sprawia, że program Visual Studio lub Unity blokuje

- **Integration**

  - Stała aktywacja wtyczki aparatu Unity po wybraniu innego edytora domyślnego.

  - Tworzenie stałego szablonu pliku aparatu Unity.

## <a name="1602"></a>1.6.0.2

Wydana 24 lipca 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Wycofanie obejścia problemu z wydajnością aparatu Unity, który został rozwiązany przez Unity.

## <a name="1601"></a>1.6.0.1

Wydanie 10 lipca 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała obsługa zabarwienia kodu programu do cieniowania.

## <a name="1600"></a>1.6.0.0

Wydanie z 26 czerwca 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Kreatorów**

  - Rozwiązano literówka z komunikatem OnApplicationFocus.

- **Generowanie projektu:**

  - Przejściowe obejście błędu wydajności aparatu Unity: wielowyspy pamięci podręcznej podczas generowania projektów.

  - Nie Konwertuj przenośnego pliku PDB na plik mdb już w przypadku korzystania z nowego środowiska uruchomieniowego aparatu Unity.

## <a name="1502"></a>1.5.0.2

Wydanie 18 kwietnia 2018

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę podstawowego uzupełniania kodu programu do cieniowania.

  - Dodano obsługę przełączania komentarzy w plikach programu do cieniowania.

## <a name="1501"></a>1.5.0.1

Wydana 28 marca 2018

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę dodatkowych szablonów w Eksploratorze projektów aparatu Unity.

## <a name="1500"></a>1.5.0.0

Wydana 21 marca 2018

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę wykrywania i dołączania do graczy systemu Android połączonych za pośrednictwem portu USB.

## <a name="1403"></a>1.4.0.3

Wydana 5 marca 2018

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę nowego generatora projektu w środowisku Unity 2018,1.

- **Integration**

  - Dodano panel opcji dla ustawień dedykowanych.

## <a name="1402"></a>1.4.0.2

Wydana 24 stycznia 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Stałe wykrywanie wersji narzędzia mono.

- **Integration**

  - Rozwiązano problemy z chronometrażem w przypadku aktywacji 2018,1 i wtyczki.

  - Naprawiono stałe powiadomienia podczas wykrywania nowego odtwarzacza.

## <a name="1401"></a>1.4.0.1

Wydanie 23 stycznia 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stałe foldery rozwijania/zwijania po dwukrotnym kliknięciu

## <a name="1400"></a>1.4.0.0

Wydanie 13 grudnia 2017

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę .NET Standard.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono automatyczną konwersję symboli debugowania w pliku PDB.

## <a name="1301"></a>1.3.0.1

Wydanie 12 grudnia 2017

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono pośrednie wywołanie EditorPrefs. getbool wpływające na inspektora podczas próby zmiany rozmiaru tablicy.

- **Kreatorów**

  - Odśwież kontekst Roslyn przed wstawieniem metody.

## <a name="1300"></a>1.3.0.0

Wydana 20 listopada 2017

### <a name="new-features"></a>Nowe funkcje

- **Kreatorów**

  - Dodano kreatora "Implementuj komunikat aparatu Unity".

  - Dodano obsługę nowego interfejsu API uzupełniania w programie VS for Mac 7,4.

## <a name="1200"></a>1.2.0.0

Wydanie 23 października 2017

### <a name="new-features"></a>Nowe funkcje

- **Oknie**

  - Dodano obsługę przenośnych plików symboli debugowania.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Stałe rozszerzenie dll zostało nieprawidłowo dodane do pliku zestawu.

  - Nie Wymuszaj flagi AllowAttachedDebuggingOfEditor Unity, ponieważ wartością domyślną jest teraz "true".

## <a name="1103"></a>1.1.0.3

Wydanie 23 października 2017

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę profilu programu .NET 4,6.

## <a name="1102"></a>1.1.0.2

Wydana 8 sierpnia 2017

### <a name="new-features"></a>Nowe funkcje

- **Oknie**

  - Uruchom okno dialogowe Dołączanie do procesu, jeśli nie masz pewności, do którego aparatu Unity chcesz dołączyć.

- **Generowanie projektu:**

  - Zawsze włączaj niebezpieczny przełącznik kompilacji, gdy jest używany aparat Unity 5,6.

## <a name="1101"></a>1.1.0.1

Wydanie 20 lipca 2017

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę zlokalizowanych zasobów.

## <a name="1100"></a>1.1.0.0

Wydana 12 lipca 2017

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę dołączania do graczy i edytorów za pomocą okna Dołącz do procesu.

- **Generowanie projektu:**

  - Stałe odwołania do nazw zestawów za pomocą plików MCS. rsp.

  - Dodano obsługę assembly.jsw jednostkach kompilacji.

  - Stałe definiuje z poziomu interfejsu API.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono komunikat o błędzie programu cieniowania podczas kompilowania.

## <a name="1001"></a>1.0.0.1

Wydana 4 maja 2017

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono aktywne śledzenie dokumentów przy użyciu hybrydowych i zwykłych projektów.

## <a name="1000"></a>1.0.0.0

Wydana 3 maja 2017
