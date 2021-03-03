---
title: Dziennik zmian (Visual Studio Tools for Unity, Windows) | Microsoft Docs
description: Wyświetl dziennik zmian dla Visual Studio Tools for Unity systemu Windows. Zobacz zmiany w wersji 1.0.0.0 przez 4.7.0.0 i poza nią.
ms.custom: ''
ms.date: 3/1/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 12a6e122d6193b7aa98cf27668dab201bbb86ce4
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683475"
---
# <a name="change-log-visual-studio-tools-for-unity-windows"></a>Dziennik zmian (Visual Studio Tools for Unity, Windows)

Visual Studio Tools for Unity dziennik zmian.

## <a name="4910"></a>4.9.1.0
Wydana 2 marca 2021

### <a name="new-features"></a>Nowe funkcje

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

  - Rozwiązano różne problemy z interfejsem użytkownika dla języków innych niż plk.

  - Rozwiązano problemy ze stabilnością dotyczące [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) diagnostyki.
  
- **Debugera**

  - Rozwiązano problemy z rozłączeniem maszyny wirtualnej podczas korzystania z `Trace` metod.

- **Sprawozdanie**

  - Stałe filtrowanie przestarzałych właściwości zgłaszających wyjątki.

## <a name="4900"></a>4.9.0.0
Wydana 20 stycznia 2021

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę `raytrace shaders` `UXML` `USS` plików i.

  - Dodano `.vsconfig` obsługę generacji. Program Visual Studio powinien teraz wykryć składniki, których brakuje, i monitować o ich zainstalowanie podczas korzystania z projektów aparatu Unity.

  - Zaktualizowano interfejs API komunikatów Unity (dla wszystkich metod używanych jako współprocedury).

  - Zaktualizowano wykrywanie Android SDK.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono proces odświeżania podczas korzystania z okna dialogowego wyboru wystąpienia.

  - Stała [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) Diagnostyka, dająca błędne ostrzeżenia dotyczące procedur współdziałania i `AssetPostprocessor.OnAssignMaterialModel` .

## <a name="4820"></a>4.8.2.0
Wydana 10 listopada 2020

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Ulepszona [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md) Diagnostyka do zastosowania do wszystkiego dziedziczonego z `Component` , a nie tylko `MonoBehaviour` .

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Rozwiązano nieprawidłową ważność komunikatów CodeLens.

## <a name="4810"></a>4.8.1.0
Wydanie 13 października 2020

### <a name="new-features"></a>Nowe funkcje

- **Sprawozdanie**

  - Dodano obsługę niejawnej konwersji z wywołaniami. Wcześniej ewaluatora wymusza dokładne sprawdzanie typów, co powoduje wyświetlenie `Failed to find a match for method([parameters...])` komunikatów ostrzegawczych.

- **Integration**

  - Dodano [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) diagnostykę. Nie należy używać `System.Reflection` funkcji w przypadku komunikatów o znaczeniu krytycznym, takich jak `Update` ,, `FixedUpdate` `LateUpdate` , lub `OnGUI` .

  - Ulepszone [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) i [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) uniemożliwione, z obsługą wszystkich `AssetPostprocessor` metod statycznych.

  - Dodano [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md) pominięcie dla elementu `CS8618` . `C# 8.0` wprowadza typy odwołań do wartości null i niedopuszczające wartości null. Wykrywanie inicjalizacji typów dziedziczących z `UnityEngine.Object` nie jest obsługiwane i spowoduje błędy.

  - Teraz korzystamy z tego samego odtwarzacza i mechanizmu generowania projektu asmdef dla obu systemów Unity 2019. x i 2020. x +.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono nieoczekiwane uzupełnienie komunikatów w komentarzach.

## <a name="4800"></a>4.8.0.0 
Wydanie 14 września 2020

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała generacja projektu odtwarzacza z użyciem aparatu Unity. x.

## <a name="4710"></a>4.7.1.0
Wydana 5 sierpnia 2020

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę przestrzeni nazw do szablonów domyślnych.
  
  - Zaktualizowano interfejs API komunikatów aparatu Unity do 2019,4.

  - Dodano [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) pominięcie dla elementu `CA1823` . Pola prywatne z `SerializeField` `SerializeReference` atrybutami lub nie powinny być oznaczone jako nieużywane (FxCop).
  
  - Dodano [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) pominięcie dla elementu `CA1822` . Komunikaty aparatu Unity nie powinny być oflagowane jako kandydaci dla `static` modyfikatora (FxCop).

  - Dodano [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) pominięcie dla elementu `CA1801` . Nie należy usuwać nieużywanych parametrów z komunikatów Unity (FxCop).
  
  - Dodano obsługę elementu MenuItem do elementu [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) pomijania.  

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawione [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) i [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) pomijające nie działają z dodatkowymi nawiasami ani z argumentami metod.
  
  - Naprawione obowiązkowe odświeżenie bazy danych zasobów, nawet jeśli funkcja AutoRefresh została wyłączona w ustawieniach aparatu Unity.

## <a name="4700"></a>4.7.0.0
Wydanie 23 czerwca 2020

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę utrwalania folderów rozwiązań, gdy aparat Unity ponownie generuje rozwiązanie i projekty.

  - Dodano [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) diagnostykę. Wykryj niepoprawną sygnaturę metody z `InitializeOnLoadMethod` `RuntimeInitializeOnLoadMethod` atrybutem or.

  - Dodano [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) diagnostykę. Użycie `Invoke` , `InvokeRepeating` , `StartCoroutine` lub `StopCoroutine` z pierwszym argumentem będącym literałem ciągu nie jest bezpieczne.

  - Dodano [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) diagnostykę. `SetPixels` wywołanie jest powolne.

  - Dodano obsługę komentarza bloku i wcięcia dla plików programu do cieniowania.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Nie należy resetować zaznaczenia podczas filtrowania komunikatów w Kreatorze komunikatów aparatu Unity.
  
  - Zawsze używaj domyślnej przeglądarki podczas otwierania dokumentacji interfejsu API aparatu Unity.
  
  - Stałe [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) i [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) pomijane z następującymi regułami: pomijanie `IDE0044` (tylko do odczytu), `IDE0051` (nieużywane), `CS0649` (nigdy nie są przypisywane) dla wszystkich pól, które mają atrybut SerializeField. Pomijaj element `CS0649` (nigdy nieprzypisane) dla pól publicznych wszystkich typów rozszerzających elementy `Unity.Object`.

  - Stałe sprawdzanie parametru typu ogólnego dla [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) diagostic.

- **Sprawozdanie**

  - Stałe porównanie równości z wyliczeniem.

## <a name="4610"></a>4.6.1.0
Wydana 19 maja 2020

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Ostrzegaj, jeśli nie można utworzyć serwera obsługi komunikatów na stronie aparatu Unity.
  
  - Prawidłowo uruchamiaj analizatory podczas kompilacji uproszczonej.
  
  - Rozwiązano problem polegający na tym, że Klasa niebehawioralna utworzona na podstawie UPE jest niezgodna z nazwą pliku.

## <a name="4600"></a>4.6.0.0
Opublikowano 14 kwietnia 2020

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę CodeLens (skryptów i komunikatów aparatu Unity).
  
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

## <a name="4510"></a>4.5.1.0

Wydana 16 marca 2020

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) pominięcie dla elementu `IDE0051` . Metody prywatne używane z metodami Invoke, InvokeRepeating, StartCoroutine lub StopCoroutine nie powinny być oznaczone jako nieużywane.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała dokumentacja OnDrawGizmos/OnDrawGizmosSelected.

- **Sprawozdanie**

  - Stała Inspekcja argumentu lambda.

## <a name="4501"></a>4.5.0.1

Wydana 19 lutego 2020

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) sprawdzenie diagnostyki dla nieprawidłowej sygnatury wiadomości. Podczas sprawdzania typów z wieloma poziomami dziedziczenia ta Diagnostyka może zakończyć się niepowodzeniem z następującym komunikatem: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="4500"></a>4.5.0.0

Wydana 22 stycznia 2020

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę plików HLSL.
  
  - Dodano [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) pominięcie dla elementu `IDE0051` . Pola prywatne z `SerializeField` atrybutem nie powinny być oznaczone jako nieużywane.
  
  - Dodano [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) pominięcie dla elementu `CS0649` . Pola z `SerializeField` atrybutem nie powinny być oznaczone jako nieprzypisane.  

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała generacja projektu ( `GenerateTargetFrameworkMonikerAttribute` element docelowy nie zawsze znajdował się poprawnie).

## <a name="4420"></a>4.4.2.0

Wydanie 3 grudnia 2019

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała Diagnostyka ze zdefiniowanymi przez użytkownika interfejsami.

  - Stałe szybkie etykietki narzędzi z nieprawidłowo sformułowanymi wyrażeniami.

## <a name="4410"></a>4.4.1.0

Wydana 6 listopada, 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę procesów w tle środowiska Unity. (Debuger może połączyć się z głównym procesem zamiast procesu podrzędnego).
  
  - Dodano szybką etykietkę narzędzia dla komunikatów aparatu Unity wyświetlającą skojarzoną dokumentację.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono analizatora porównywania tagów [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md) za pomocą zaawansowanych wyrażeń binarnych i wywołań.

### <a name="deprecated-features"></a>Przestarzałe funkcje

- **Integration**

  - W przyszłości program Visual Studio Tools for Unity obsługuje tylko program Visual Studio 2017 +.

## <a name="4400"></a>4.4.0.0

Wydanie 15 października 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) pominięcie dla `IDE0060` (nieużywany parametr) dla wszystkich komunikatów aparatu Unity.
  
  - Dodano szybką etykietkę narzędzia dla pól otagowanych za pomocą `TooltipAttribute` . (Ta wartość będzie działała w przypadku prostej metody dostępu get używającej również tego pola).

## <a name="4330"></a>4.3.3.0

Wydanie 23 września, 2019

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono raportowanie błędów i ostrzeżeń dotyczących uproszczonych kompilacji.

## <a name="4320"></a>4.3.2.0

Wydanie 16 września 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Wyjaśniono, że program Visual Studio obsługuje projekty Unity przez dodanie nowej diagnostyki specyficznej dla aparatu Unity. Wprowadziliśmy również zmiany powodujące, że środowisko IDE działa teraz bardziej inteligentnie dzięki pomijaniu ogólnej diagnostyki języka C#, która nie dotyczy projektów Unity. Na przykład IDE nie będzie wyświetlał szybkiej poprawki, aby zmienić zmienną inspektora, do `readonly` której nie można zmodyfikować zmiennej w edytorze aparatu Unity.
    - [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md): Komunikaty aparatu Unity są wywoływane przez środowisko uruchomieniowe, nawet jeśli są puste, nie deklaruj ich, aby uniknąć przetwarzania uncesseray przez środowisko uruchomieniowe aparatu Unity.
    - [`UNT0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0002.md): Porównanie tagów przy użyciu równości ciągów jest wolniejsze niż wbudowana Metoda CompareTag.
    - [`UNT0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0003.md): Użycie ogólnego formularza GetComponent jest preferowane dla bezpieczeństwa typu.
    - [`UNT0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0004.md): Komunikat aktualizacji jest zależny od szybkości ramki i powinien używać czasu deltaTime zamiast czasu. fixedDeltaTime.
    - [`UNT0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0005.md): Komunikat FixedUpdate jest niezależny od szybkości klatek i powinien używać Time. fixedDeltaTime zamiast Time. deltaTime.
    - [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md): Wykryto niepoprawną sygnaturę metody dla tego komunikatu aparatu Unity.
    - [`UNT0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0007.md): Unity zastępuje operator porównania null dla obiektów Unity, które są niezgodne z łączeniem zerowym.
    - [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md): Unity zastępuje operator porównania null dla obiektów Unity, które są niezgodne z propagacją wartości null.
    - [`UNT0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0009.md): W przypadku zastosowania atrybutu InitializeOnLoad do klasy należy dostarczyć statyczny Konstruktor. Atrybut InitializeOnLoad zapewnia, że zostanie on wywołany podczas uruchamiania edytora.
    - [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md): Działania bezdziałające powinny być tworzone tylko przy użyciu AddComponent (). MonoBehaviour to składnik, który musi zostać dołączony do obiektu GameObject.
    - [`UNT0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0011.md): ScriptableObject powinien być utworzony tylko przy użyciu metody CreateInstance (). Obiekt ScriptableObject musi zostać utworzony przez aparat Unity do obsługi metod komunikatów aparatu Unity.
    - [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) dla `IDE0029` : obiekty Unity nie powinny używać łączenia zerowego.
    - [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) dla `IDE0031` : obiekty Unity nie powinny używać propagacji o wartości null.
    - [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) dla `IDE0051` : komunikaty aparatu Unity są wywoływane przez środowisko uruchomieniowe aparatu Unity.
    - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) dla `IDE0044` : pola z atrybutem SerializeField nie powinny być tylko do odczytu.

## <a name="4310"></a>4.3.1.0

Wydanie 4 września 2019

### <a name="new-features"></a>Nowe funkcje

- **Sprawozdanie**

  - Dodano obsługę wyświetlania lepszych typów, tj. `List<object>` zamiast `List'1[[System.Object, <corlib...>]]` .

  - Dodano obsługę dostępu do elementu członkowskiego wskaźnika, `p->data->member` tj.

  - Dodano obsługę niejawnych konwersji w inicjatorach tablicy, tj `new byte [] {1,2,3,4}` .

## <a name="4300"></a>4.3.0.0

Opublikowano 13 sierpnia 2019

### <a name="new-features"></a>Nowe funkcje

- **Oknie**

  - Dodano obsługę protokołu MDS 2,51.

- **Integration**

  - Udoskonalono okno "Dołączanie do wystąpienia aparatu Unity" z funkcjami sortowania, wyszukiwania i odświeżania. Identyfikator PID jest teraz wyświetlany nawet dla graczy lokalnych (przez przeszukiwanie gniazd nasłuchujących w systemie w celu pobrania procesu będącego właścicielem).

  - Dodano obsługę plików asmdef.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała obsługa nieprawidłowych komunikatów podczas komunikowania się z graczami aparatu Unity.

- **Sprawozdanie**

  - Stała obsługa przestrzeni nazw w wyrażeniach.

  - Stała Inspekcja przy użyciu typów IntPtr.
  
  - Rozwiązywanie problemów z wyjątkami.

  - Stała Ocena identyfikatorów pseudo (takich jak $exception).

  - Zapobiegaj awarii podczas usuwania odwołań do nieprawidłowych adresów.  

  - Rozwiązano problem z niezaładowanymi domenami aplikacji.

## <a name="4201"></a>4.2.0.1

Wydana 24 lipca 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano nową opcję w celu utworzenia dowolnego typu plików z Eksploratora projektów aparatu Unity.
  
  - Popraw buforowanie diagnostyczne podczas korzystania z szybkich kompilacji dla projektów Unity.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Rozwiązano problem, gdy rozszerzenie pliku nie zostało obsłużone przez dowolny dobrze znany Edytor.

  - Stała obsługa rozszerzeń niestandardowych w Eksploratorze projektów aparatu Unity.

  - Naprawiono ustawienia zapisywania poza głównym oknem dialogowym.

  - Usunięto starszą zależność Microsoft. VisualStudio. MPF.

## <a name="4110"></a>4.1.1.0

Wydana 24 maja 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Zaktualizowano interfejs API o bezzachowań do 2019,1.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono ostrzeżenia i błędy raportowane w przypadku włączenia uproszczonej kompilacji.

  - Stała wydajność lekkiej kompilacji.

## <a name="4100"></a>4.1.0.0

Wydana 21 maja 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę nowego interfejsu API usługi Batch do szybszego ponownego ładowania projektów.

  - Wyłączono pełną kompilację dla projektów środowiska Unity, na korzyść używania błędów i ostrzeżeń funkcji IntelliSense. Istotny aparat Unity tworzy rozwiązanie programu Visual Studio z projektami biblioteki klas, które reprezentują, co Unity działa wewnętrznie. Z tego powodu wynik kompilacji w programie Visual Studio nigdy nie jest używany lub nie jest wybierany przez środowisko Unity, ponieważ ich potok kompilacji jest zamknięty. Kompilowanie w programie Visual Studio jest samo zużywanie zasobów. Jeśli potrzebujesz pełnej kompilacji, ponieważ masz narzędzia lub Instalatora, które od niego zależą, możesz wyłączyć tę optymalizację (Narzędzia/Opcje/narzędzia dla aparatu Unity/wyłączyć pełną kompilację projektów).

  - Automatycznie pokazuj Eksplorator projektów środowiska Unity (UPE) po załadowaniu projektu środowiska Unity. UPE zostanie zadokowany obok Eksplorator rozwiązań.

  - Zaktualizowany mechanizm wyodrębniania nazw projektów z użyciem aparatu Unity. x.

  - Dodano obsługę pakietów Unity w UPE. Widoczne są tylko pakiety, do których istnieją odwołania (przy użyciu manifest.jsw `Packages` folderze) i pakiety lokalne (osadzone w `Packages` folderze).

- **Generowanie projektu:**

  - Zachowaj właściwości zewnętrzne podczas przetwarzania pliku rozwiązania.

- **Sprawozdanie**

  - Dodano obsługę nazw kwalifikowanych aliasem (tylko globalna przestrzeń nazw dla teraz). Dlatego ewaluatora wyrażeń akceptuje teraz typy przy użyciu formularza Global:: Namespace. Type.

  - Dodano obsługę `pointer[index]` formularza, która jest semantycznie identyczna z formularzem dereferencji wskaźnika `*(pointer+index)` .

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Rozwiązano problemy zależności z Microsoft. VisualStudio. MPF.

  - Stała dołączanie odtwarzacza platformy UWP bez załadowania żadnego projektu.

  - Naprawiono automatyczne odświeżenie bazy danych zasobów, gdy program Visual Studio nie został jeszcze dołączony.

  - Rozwiązano problemy motywu z etykietami i polami wyboru.

- **Oknie**

  - Naprawiono wykonywanie kroków przy użyciu konstruktorów statycznych.

## <a name="4005"></a>4.0.0.5

Wydana 27 lutego 2019

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Rozwiązano wykrywanie wersji programu Visual Studio za pomocą pakietu instalacyjnego.

  - Usunięto nieużywane zestawy z pakietu instalacyjnego.

## <a name="4004"></a>4.0.0.4

Wydanie 13 lutego 2019

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę w celu prawidłowego wykrywania procesów Unity podczas instalacji i Zezwalanie aparatowi instalacji na lepsze obsłudze blokad plików.

  - Zaktualizowano `ScriptableObject` interfejs API.

## <a name="4003"></a>4.0.0.3

Wydanie 31 stycznia 2019

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Pola publiczne i serializowane nie będą już powodowały ostrzeżeń. `CS0649` `IDE0051` W projektach Unity, które utworzyły te komunikaty, zostały pominięte ostrzeżenia kompilatora.

- **Integration**

  - Ulepszono środowisko użytkownika do wyświetlania wystąpień edytora i odtwarzacza Unity (system Windows jest teraz zmieniany, użyj jednolitych marginesów i Wyświetl uchwyt zmiany rozmiaru). Dodano Process-Id informacji dla edytorów aparatu Unity.

  - Zaktualizowano `MonoBehaviour` interfejs API.

- **Sprawozdanie**

  - Dodano obsługę funkcji lokalnych.

  - Dodano obsługę pseudo zmiennych (wyjątków i identyfikatorów obiektów).

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Rozwiązano problem z obrazami i motywami monikerów.

  - Podczas autoodświeżania bazy danych zasobów należy zapisywać do Okno Dane wyjściowe podczas debugowania.

  - Stałe opóźnienia interfejsu użytkownika przy filtrowaniu kreatora.

- **Oknie**

  - Stały odczyt atrybutu niestandardowego dla nazwanych argumentów w przypadku używania starych wersji protokołu.

## <a name="4002"></a>4.0.0.2

Wydanie 23 stycznia 2019

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono eksperymentalną generację kompilacji.

  - Stała obsługa zdarzeń w pliku projektu w celu zminimalizowania siły interfejsu użytkownika.

  - Dostawca stałego uzupełniania z wsadowymi zmianami tekstu.

- **Oknie**

  - Naprawiono wyświetlanie komunikatów debugowania użytkownika w dołączonym debugerze.

## <a name="4001"></a>4.0.0.1

Wydanie 10 grudnia 2018

### <a name="new-features"></a>Nowe funkcje

- **Sprawozdanie**

  - Zamieniono NRefactory na korzyść Roslyn na potrzeby oceny wyrażenia.

  - Dodano obsługę wskaźników: dereferencja, rzutowania lub arytmetycznego wskaźnika (w tym celu wymagane są zarówno środowisko Unity 2018.2 + i nowe środowisko uruchomieniowe).

  - Dodano obsługę widoku wskaźnika tablicy (na przykład w języku C++). Wypełnij wyrażenie wskaźnika, a następnie Dołącz przecinek i liczbę elementów, które chcesz zobaczyć.

  - Dodano obsługę konstrukcji asynchronicznych.

- **Integration**

  - Dodano obsługę automatycznego odświeżania bazy danych zasobów aparatu Unity przy zapisywaniu. Ta funkcja jest domyślnie włączona i wyzwala ponowną kompilację po stronie aparatu Unity podczas zapisywania skryptu w programie Visual Studio. Tę funkcję można wyłączyć w programie Tools\Options\Tools for Unity\Refresh Unity AssetDatabase przy zapisywaniu.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała aktywacja mostka, gdy program Visual Studio nie jest wybrany jako preferowany edytor zewnętrzny.

  - Obliczanie stałych wyrażeń z nieprawidłowo sformułowanymi lub nieobsługiwanymi wyrażeniami.

## <a name="4000"></a>4.0.0.0

Wydanie 4 grudnia 2018

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Dodano obsługę programu Visual Studio 2019 (potrzebujesz co najmniej aparatu Unity 2018,3, aby można było używać programu Visual Studio 2019 jako zewnętrznego edytora skryptów).

  - Przyjęto, że usługa obrazów programu Visual Studio i wykaz mają pełną obsługę skalowania HDPI, obrazów doskonałych pikseli i motywów.

### <a name="deprecated-features"></a>Przestarzałe funkcje

- **Integration**

  - Przechodząc do przodu, Visual Studio Tools for Unity będzie obsługiwał tylko środowisko Unity 5.2 + (z wbudowaną integracją programu Visual Studio).

  - W przyszłości program Visual Studio Tools for Unity obsługuje tylko program Visual Studio 2015 +.

  - Usunięto starszą wersję usługi językowej, listę błędów i pasek stanu.

  - Usunięto Kreatora szybkiego działania (na korzyść dedykowanej obsługi technologii IntelliSense).

## <a name="3903"></a>3.9.0.3

Wydana 28 listopada 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stałe ponowne ładowanie projektu i problemy z technologią IntelliSense podczas dodawania lub usuwania skryptów znajdujących się w pierwszym projekcie.

## <a name="3902"></a>3.9.0.2

Wydana 19 listopada 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Oknie**

  - Naprawiono zakleszczenie w bibliotece używanej do komunikacji z aparatem debugera aparatu Unity, co sprawia, że program Visual Studio lub Unity blokuje

## <a name="3901"></a>3.9.0.1

Wydana 15 listopada 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stała aktywacja wtyczki aparatu Unity po wybraniu innego edytora domyślnego.

## <a name="3900"></a>3.9.0.0

Wydana 13 listopada 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Wycofanie obejścia problemu z wydajnością aparatu Unity, który został rozwiązany przez Unity.

## <a name="3807"></a>3.8.0.7

Wydanie 20 września 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Oknie**

  - (Przewoźny z 3.9.0.2) Naprawiono zakleszczenie w bibliotece używanej do komunikacji z aparatem debugera aparatu Unity, co sprawia, że program Visual Studio lub Unity blokuje

## <a name="3806"></a>3.8.0.6

Wydana 27 sierpnia 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stałe ponowne ładowanie projektów i rozwiązań.

## <a name="3805"></a>3.8.0.5

Wydana 20 sierpnia 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stałe usuwanie subskrypcji monitorowania projektu.

## <a name="3804"></a>3.8.0.4

Wydanie 14 sierpnia 2018

### <a name="new-features"></a>Nowe funkcje

- **Sprawozdanie**

  - Dodano obsługę wartości wskaźnika.

  - Dodano obsługę metod ogólnych.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Inteligentne ponowne załadowanie z wieloma projektami zostało zmienione.

## <a name="3803"></a>3.8.0.3

Wydana 24 lipca 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - (Przewoźny z 3.9.0.0) Wycofanie obejścia problemu z wydajnością aparatu Unity, który został rozwiązany przez Unity.

## <a name="3802"></a>3.8.0.2

Wydana 7 lipca 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Przejściowe obejście błędu wydajności aparatu Unity: wielowyspy pamięci podręcznej podczas generowania projektów.

## <a name="3801"></a>3.8.0.1

Wydanie z 26 czerwca 2018

### <a name="new-features"></a>Nowe funkcje

- **Debugera**

  - Dodano obsługę poleceń UserLog i UserBreak.

  - Dodano obsługę typu z opóźnieniem (Optymalizacja opóźnienia odpowiedzi na obciążenie sieci i debuger).

### <a name="bug-fixes"></a>Poprawki błędów

- **Sprawozdanie**

  - Ulepszona Ocena wyrażenia operatora binarnego i wyszukiwanie metod.

## <a name="3800"></a>3.8.0.0

Wydana 30 maja 2018

### <a name="new-features"></a>Nowe funkcje

- **Debugera**

  - Dodano obsługę wyświetlania zmiennych w konstrukcjach asynchronicznych.

  - Dodano obsługę przetwarzania zagnieżdżonych typów podczas ustawiania punktów przerwania, aby zapobiec występowaniu ostrzeżeń z konstrukcjami kompilatora.

- **Integration**

  - Dodano obsługę gramatyki deautomatyzujące dla programów do cieniowania (obciążenie języka C++ nie jest już potrzebne do zabarwienia kodu programu do cieniowania).

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Nie Konwertuj przenośnego pliku PDB na plik mdb już w przypadku korzystania z nowego środowiska uruchomieniowego aparatu Unity.

## <a name="3701"></a>3.7.0.1

Wydana 7 maja 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Instalatora**

  - Problem związany z zależnością podczas korzystania z kompilacji eksperymentalnej.

## <a name="3700"></a>3.7.0.0

Wydana 7 maja 2018

### <a name="new-features"></a>Nowe funkcje

- **Debugera**

  - Dodano obsługę debugowania zorganizowanego (debugowanie wielu graczy/edytorów z tą samą sesją programu Visual Studio).

  - Dodano obsługę debugowania odtwarzacza USB systemu Android.

  - Dodano obsługę debugowania odtwarzacza platformy UWP/IL2CPP.

- **Sprawozdanie**

  - Dodano obsługę specyfikatorów szesnastkowych.

  - Udoskonalone środowisko oceny okna Czujka.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stałe użycie ustawień wyjątków.

- **Generowanie projektu:**

  - Wyklucz jednostki kompilacji Menedżera pakietów z generacji.

## <a name="3605"></a>3.6.0.5

Wydana 13 marca 2018

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę nowego generatora projektu w środowisku Unity 2018,1.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Stałe obsługiwanie Stanów uszkodzonych z projektami niestandardowymi.

- **Oknie**

  - Naprawiono ustawienie następnej instrukcji.

## <a name="3604"></a>3.6.0.4

Wydana 5 marca 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Stałe wykrywanie wersji narzędzia mono.

- **Integration**

  - Rozwiązano problemy z chronometrażem w przypadku aktywacji 2018,1 i wtyczki.

## <a name="3603"></a>3.6.0.3

Wydanie 23 lutego 2018

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę .NET Standard.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Stałe wykrywanie platformy docelowej aparatu Unity.

- **Oknie**

  - Naprawiono uszkodzenie wyjątków, które są zgłaszane poza userCode.

## <a name="3602"></a>3.6.0.2

Wydana 7 lutego 2018

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Aktualizuj powierzchnię interfejsu API UnityMessage dla 2017,3.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Załaduj ponownie tylko projekty dla zmiany zewnętrznej (z ograniczeniami).

## <a name="3601"></a>3.6.0.1

Wydana 24 stycznia 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono automatyczną konwersję symboli debugowania w pliku PDB.

  - Naprawiono pośrednie wywołanie EditorPrefs. getbool wpływające na inspektora podczas próby zmiany rozmiaru tablicy.

## <a name="3600"></a>3.6.0.0

Wydanie 10 stycznia 2018

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę modelu referencyjnego wielowyspy 2018,1.

- **Sprawozdanie**

  - Dodano obsługę identyfikatora $exception.

- **Oknie**

  - Dodano obsługę atrybutów DebuggerHidden/DebuggerStepThrough z nowym środowiskiem uruchomieniowym aparatu Unity.

- **Kreatorów**

  - Wprowadź wersję "Najnowsza" dla kreatorów.

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Stałe obliczanie identyfikatorów GUID projektu dla projektów odtwarzacza.

- **Oknie**

  - Naprawiono rasę w obsłudze zdarzeń przerwania.

- **Kreatorów**

  - Odśwież kontekst Roslyn przed wstawieniem metody.

## <a name="3503"></a>3.5.0.3

Wydanie 9 stycznia 2018

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Naprawiono automatyczną konwersję symboli debugowania w pliku PDB.

## <a name="3502"></a>3.5.0.2

Wydanie 4 grudnia 2017

### <a name="new-features"></a>Nowe funkcje

- **Integration**

  - Projekty Unity są teraz automatycznie ponownie ładowane w programie Visual Studio po dodaniu skryptu do środowiska Unity lub jego usunięciu.

- **Oknie**

  - Dodano opcję, aby użyć debugera mono udostępnionego przez platformę Xamarin i Visual Studio dla komputerów Mac do debugowania edytora aparatu Unity.

  - Dodano obsługę przenośnych plików symboli debugowania.

### <a name="bug-fixes"></a>Poprawki błędów

- **Integration**

  - Rozwiązano problemy dotyczące zależności instalacji.

  - Menu Pomoc interfejsu API stałego aparatu Unity nie jest wyświetlane.

- **Generowanie projektu:**

  - Stała generacja projektu odtwarzacza podczas pracy z platformy UWPą z zapleczem IL2CPP/. NET 4,6.

  - Stałe rozszerzenie dll zostało nieprawidłowo dodane do pliku zestawu.

  - Stałe użycie określonego poziomu zgodności interfejsu API projektu zamiast globalnego.

  - Nie Wymuszaj flagi AllowAttachedDebuggingOfEditor Unity, ponieważ wartością domyślną jest teraz "true".

## <a name="3402"></a>3.4.0.2

Wydana 19 września 2017

### <a name="new-features"></a>Nowe funkcje

- **Generowanie projektu:**

  - Dodano obsługę assembly.jsw jednostkach kompilacji.

  - Zatrzymano kopiowanie zestawów Unity do folderu projektu.

- **Oknie**

  - Dodano obsługę ustawiania następnej instrukcji przy użyciu nowego środowiska uruchomieniowego aparatu Unity.

  - Dodano obsługę typu decimal z nowym środowiskiem uruchomieniowym aparatu Unity.

  - Dodano obsługę konwersji niejawnych/jawnych.

### <a name="bug-fixes"></a>Poprawki błędów

- **Sprawozdanie**

  - Stałe tworzenie tablicy z niejawnym rozmiarem.

  - Stałe elementy generowane przez kompilator z elementami lokalnymi.

- **Generowanie projektu:**

  - Naprawiono odwołanie do programu Microsoft. CSharp for 4,6 — poziom interfejsu API.

## <a name="3302"></a>3.3.0.2

Wydanie 15 sierpnia 2017

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Rozwiązano generowanie rozwiązania Visual Studio dla aparatu Unity 5,5 i poprzednich wersji.

## <a name="3300"></a>3.3.0.0

Wydanie 14 sierpnia 2017

### <a name="new-features"></a>Nowe funkcje

- **Sprawozdanie**

  - Dodano obsługę tworzenia struktur przy użyciu nowego środowiska uruchomieniowego aparatu Unity.

  - Dodano obsługę minimalistyczny dla wskaźników.

### <a name="bug-fixes"></a>Poprawki błędów

- **Sprawozdanie**

  - Stałe wywołanie metody dla elementów podstawowych.

  - Stała Ocena pola z typami oznaczonymi przez BeforeFieldInit.

  - Rozwiązano nieobsługiwane wywołania z operatorami dwuargumentowymi (Substract).

  - Rozwiązano problemy podczas dodawania elementów do czujki programu Visual Studio.

- **Generowanie projektu:**

  - Stałe odwołania do nazw zestawów za pomocą plików MCS. rsp.

  - Stałe definiuje z poziomu interfejsu API.

## <a name="3200"></a>3.2.0.0

Wydana 10 maja 2017

### <a name="new-features"></a>Nowe funkcje

- **Instalatora**

  - Dodano obsługę czyszczenia pamięci podręcznej MEF.

### <a name="bug-fixes"></a>Poprawki błędów

- **Edytor kodu:**

  - Stała Klasyfikacja/uzupełnianie z atrybutami niestandardowymi.

  - Naprawiono migotanie przy użyciu komunikatów aparatu Unity.

## <a name="3100"></a>3.1.0.0

Wydana 7 kwietnia 2017

### <a name="new-features"></a>Nowe funkcje

- **Oknie**

  - Dodano obsługę nowego środowiska uruchomieniowego aparatu Unity (zgodność z programem .NET 4,6/C# 6).

- **Generowanie projektu:**

  - Dodano obsługę profilu programu .NET 4,6.

  - Dodano obsługę plików MCS. rsp.

  - Zawsze włączaj niebezpieczny przełącznik kompilacji, gdy jest używany aparat Unity 5,6.

  - Dodano obsługę generowania projektu "Player" podczas korzystania z platformy sklepu Windows i zaplecza il2cpp.

### <a name="bug-fixes"></a>Poprawki błędów

- **Edytor kodu:**

  - Stała pozycja karetki po wstawieniu metody z funkcją automatycznego uzupełniania.

- **Generowanie projektu:**

  - Usunięto przetwarzanie końcowe w wersji zestawu.

## <a name="3001"></a>3.0.0.1

Wydana 7 marca 2017

### <a name="this-version-includes-all-new-features-and-bug-fixes-introduced-with-28x-series"></a>Ta wersja zawiera wszystkie nowe funkcje i poprawki błędów wprowadzone z serii 2.8. x.

## <a name="2820---30-preview-3"></a>2.8.2.0 — wersja zapoznawcza 3 3,0
Wydana 25 stycznia 2017

### <a name="bug-fixes"></a>Poprawki błędów

- **Generowanie projektu:**

  - Stała regresja, w której projekty wtyczek, do których odwołuje się dwa razy, najpierw jako binarna Biblioteka DLL, jako odwołanie do projektu.

## <a name="2810---30-preview-2"></a>2.8.1.0 — wersja zapoznawcza 2 3,0
Wydanie 23 stycznia 2017

### <a name="bug-fixes"></a>Poprawki błędów

- **Edytor kodu:**

  - Naprawiono awarię podczas uruchamiania deklaracji atrybutu bez ukończenia nawiasu klamrowego.

- **Oknie**

  - Stałe punkty przerwania funkcji z procedurami w ramach nowego kompilatora/środowiska uruchomieniowego aparatu Unity.

  - Dodano ostrzeżenie w przypadku niemożliwego do powiązania punktu przerwania (gdy nie znaleziono odpowiedniej lokalizacji źródłowej).

- **Generowanie projektu:**

  - Stała generacja csproj z znakami specjalnymi/zlokalizowanymi.

  - Stałe odwołania poza zasobami, takie jak biblioteka (na przykład zestaw SDK usługi Facebook).

- **Różne**

  - Dodano sprawdzenie, aby uniemożliwić uruchomienie aparatu Unity podczas instalowania lub odinstalowywania.

  - Przełączono do protokołu HTTPS, aby uzyskać dostęp do dokumentacji zdalnej aparatu Unity.

## <a name="2800---30-preview"></a>2.8.0.0 — wersja zapoznawcza 3,0
Wydana 17 listopada 2016

### <a name="new-features"></a>Nowe funkcje

- **Główny**

  - Dodano obsługę Instalatora programu Visual Studio 2017.

  - Dodano obsługę rozszerzenia programu Visual Studio 2017.

  - Dodano obsługę lokalizacji.

- **Edytor kodu:**

  - Dodano funkcję IntelliSense języka C# dla komunikatów aparatu Unity.

  - Dodano barwienie kodu w języku C# dla komunikatów aparatu Unity.

- **Oknie**

  - Dodano obsługę dla `is` , `as` , bezpośrednie rzutowanie `default` , `new` wyrażenia.

  - Dodano obsługę wyrażeń łączenia ciągów.

  - Dodano obsługę wyświetlania szesnastkowych wartości liczb całkowitych.

  - Dodano obsługę tworzenia nowych zmiennych tymczasowych (instrukcji).

  - Dodano obsługę niejawnych konwersji pierwotnych.

  - Dodano lepsze komunikaty o błędach, gdy typ jest oczekiwany lub nie został znaleziony.

- **Generowanie projektu:**

  - Usunięto sufiks CSharp z nazw projektów.

  - Usunięto odwołanie do pliku TARGETS całego programu MSBuild.

- **Kreatorów**

  - Dodano obsługę komunikatów Unity w typach bez zachowań, takich jak edytor lub EditorWindow.

  - Przełączono do Roslyn, aby wprowadzić i sformatować komunikaty aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

- **Oknie**

  - Naprawiono awarię aparatu Unity podczas oceniania typów ogólnych.

  - Stała obsługa typów dopuszczających wartość null.

  - Stała obsługa typów wyliczeniowych.

  - Stała obsługa zagnieżdżonych typów elementów członkowskich.

  - Stały dostęp indeksatora kolekcji.

  - Stała obsługa debugowania ramek iteratora przy użyciu nowego kompilatora języka C#.

- **Generowanie projektu:**

  - Naprawiono usterkę, która uniemożliwiła kompilację w przypadku przekierowania do odtwarzacza sieci Web Unity.

  - Naprawiono usterkę, która uniemożliwiła kompilację podczas kompilowania skryptu z nazwą pliku zakodowanego w sieci Web.

## <a name="2300"></a>2.3.0.0

Wydanie 14 lipca 2016

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

## <a name="2200"></a>2.2.0.0

Wydana 4 lutego 2016

### <a name="new-features"></a>Nowe funkcje

- **Kreatorów**

  - Dodano inteligentne wyszukiwanie w kreatorze **Implementuj działanie** .

  - Zapoznaj się z kontekstem kreatorów; na przykład komunikaty NetworkBehavior są dostępne tylko podczas pracy z NetworkBehavior.

  - Dodano obsługę komunikatów NetworkBehavior w kreatorach.

- **INTERFEJSU użytkownika**

  - Dodano opcję konfigurowania widoczności komunikatów z zachowaniem aktywności.

  - Usunięto strony właściwości programu Visual Studio, które nie są istotne dla projektów Unity.

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

## <a name="2100"></a>2.1.0.0

Wydanie 8 września 2015

### <a name="new-features"></a>Nowe funkcje

- Obsługa aparatu Unity 5,2

### <a name="bug-fixes"></a>Poprawki błędów

- Elementy menu wyświetlania w aparacie Unity < 4,2

- Komunikat o błędzie nie jest już wyświetlany, gdy program Visual Studio blokuje pliki IntelliSense XML.

- Obsłuż <\<When Changed>> warunkowe punkty przerwania, gdy argument warunkowy nie jest wartością logiczną.

- Stałe odwołania do zestawów UnityEngine i UnityEditor dla aplikacji ze sklepu Windows.

- Naprawiono błąd podczas wykonywania w debugerze: nie można wykonać kroku, ogólny wyjątek.

- Stałe punkty przerwania liczby trafień w programie Visual Studio 2015.

## <a name="2000"></a>2.0.0.0

Wydanie 20 lipca 2015

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

## <a name="1990---20-preview-2"></a>1.9.9.0 — wersja zapoznawcza 2 2,0
Wydanie 2 kwietnia 2015

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

## <a name="1980---20-preview"></a>1.9.8.0 — wersja zapoznawcza 2,0
Wydana 12 listopada 2014

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

## <a name="1920"></a>1.9.2.0

Wydana 9 października 2014

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

## <a name="1910"></a>1.9.1.0

Wydana 22 września, 2014

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

## <a name="1900"></a>1.9.0.0

Wydana 29 lipca 2014

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

## <a name="1820"></a>1.8.2.0

Wydana 7 stycznia 2014

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

## <a name="1810"></a>1.8.1.0

Wydana 21 listopada 2013

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

## <a name="1800"></a>1.8.0.0

Wydanie 24 września 2013

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

## <a name="1220"></a>1.2.2.0

Wydanie 9 lipca 2013

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

## <a name="1210"></a>1.2.1.0

Wydanie 9 kwietnia 2013

### <a name="bug-fixes"></a>Poprawki błędów

- Stałe lokalne wdrożenie zestawów Unity do uzupełniania kodu w przypadku błędu we/wy (na przykład plików tylko do odczytu lub plików zablokowanych przez program Visual Studio).

- Naprawiono regresję, w której otwieranie skryptu z aparatu Unity nie spowoduje skoncentrowania się na pliku, jeśli został on już otwarty w programie Visual Studio.

- Rozwiązano problem z wydajnością nowej obsługi wyjątków.

- Stałe powiązania punktów przerwania w niektórych zewnętrznych bibliotekach DLL.

## <a name="1200"></a>1.2.0.0

Wydana 25 marca, 2013

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

## <a name="1100---beta-release"></a>1.1.0.0 — wydanie beta
Wydana w marcu, 9, 2013

## <a name="10130"></a>1.0.13.0
Wydana 21 stycznia 2013

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

## <a name="10120"></a>1.0.12.0
Wydanie 3 stycznia 2013

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono blokowanie programu Visual Studio, które mogło się zdarzyć, gdy program Visual Studio usunie punkt przerwania.

- Rozwiązano problem polegający na tym, że niektóre punkty przerwania nie zostaną trafione po ponownym skompilowaniu skryptów aparatu Unity.

- Rozwiązano debuger, aby prawidłowo powiadamiał program Visual Studio, gdy punkty przerwania zostały anulowane.

- Rozwiązano problem z rejestracją, który może uniemożliwić debugerowi programu Visual Studio debugowanie programów natywnych.

- Rozwiązano wyjątek, który może wystąpić podczas oceny wyrażeń UnityScript i boo.

- Naprawiono regresję, w której zmiana poziomu interfejsu API platformy .NET w aparacie Unity nie spowoduje wyzwolenia aktualizacji plików projektu.

- Naprawiono błąd interfejsu API, gdzie kod użytkownika nie może uczestniczyć w obsłudze wywołania zwrotnego dziennika.

## <a name="10110"></a>1.0.11.0
Wydana 28 listopada 2012

### <a name="new-features"></a>Nowe funkcje

- Oficjalne wsparcie dla aparatu Unity 4.

- Manipulowanie skryptami z Eksploratora projektów środowiska Unity.

- Integracja w programie Visual Studio — przejdź do okna.

- Analizowanie komunikatu konsoli informacyjnej, aby kliknięcie w Lista błędów do pierwszej StackFrame z symbolami.

- Dodaj [interfejs API](extensibility/customize-project-files-created-by-vstu.md) , aby umożliwić użytkownikowi uczestnictwo w generowaniu projektu.

- Dodaj [interfejs API](extensibility/share-the-unity-log-callback-with-vstu.md) , aby umożliwić użytkownikom uczestnictwo w LogCallback.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono regresję w tle Eksploratora projektów aparatu Unity w programie Visual Studio 2012.

- Stała generacja projektu dla użytkowników pełnego profilu platformy .NET.

- Stała generacja projektu dla użytkowników obiektu docelowego sieci Web.

- Stała generacja projektu obejmująca symbole kompilacji debugowania i śledzenia jako aparat Unity.

- Naprawiono awarię w przypadku używania znaków specjalnych w naszym oknie symbolu przejdź do.

- Naprawiono awarię, jeśli nie możemy wstrzyknąć naszej ikony na pasku stanu programu Visual Studio.

## <a name="10100"></a>1.0.10.0
Wydana 9 października 2012

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono tło Eksploratora projektów aparatu Unity w programie Visual Studio 2010.

- Rozwiązano blokadę programu Visual Studio, która może wystąpić, jeśli UnityVS próbował podłączyć debuger do aparatu Unity, którego interfejs debugera wcześniej uległ awarii.

- Naprawiono zablokowanie programu Visual Studio, który może mieć miejsce, gdy punkt przerwania został ustawiony i wystąpił ponowny ładowanie elementu AppDomain.

- Ustalono, jak zestawy są pobierane z aparatu Unity, aby uniknąć zablokowania plików i pomylić proces kompilacji aparatu Unity.

## <a name="1090"></a>1.0.9.0

Wydanie 3 października 2012

### <a name="bug-fixes"></a>Poprawki błędów

- Stała generacja projektu, gdy projekt Unity zawiera rzeczywiste zasoby JavaScript.

- Naprawiono obsługę błędów podczas obliczania wyrażenia.

- Naprawiono nowe wartości dla pól typu wartości.

- Stałe możliwe efekty uboczne po umieszczeniu wskaźnika myszy na wyrażeniach z edytora kodu.

- Naprawiono sposób, w jaki typy są przeszukiwane w załadowanych zestawach do oceny wyrażenia.

- Stała usterka UVS-21: Obliczanie przydziału obiektów Unity nie ma żadnego wpływu.

- Naprawiono usterkę UVS-21: nieprawidłowy wskaźnik podczas oceniania wywołania metody do interfejsu API Math aparatu Unity.

## <a name="1080"></a>1.0.8.0

Wydanie 26 września 2012

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono sposób, w jaki nasz program do otwierania skryptów uzyskał ścieżkę do projektu, aby upewnić się, że jest w stanie otworzyć zarówno program Visual Studio, jak i skrypty.

- Naprawiono usterkę z punktami przerwania utworzonymi podczas działania sesji debugowania, która może spowodować zablokowanie programu Visual Studio.

- Ustalono, jak UnityVS jest zarejestrowany w programie Visual Studio 2010.

## <a name="1070"></a>1.0.7.0

Wydanie 14 września 2012

### <a name="new-features"></a>Nowe funkcje

- Obsługa programu Visual Studio 2012.

### <a name="bug-fixes"></a>Poprawki błędów

- Stała generacja plików projektu edytora i wtyczek, aby dopasować zachowanie aparatu Unity.

- Naprawiono tłumaczenie symboli. pdb w aparacie Unity 4.

> [!IMPORTANT]
> Ze względu na pomoc techniczną dla programu Visual Studio 2012 należy zmienić nazwę kilku plików i przenieść inne. Pakiet UnityVS do zaimportowania aparatu Unity ma teraz nazwę UnityVS 2010 lub UnityVS 2012 dla odpowiednio programu Visual Studio 2010 i Visual Studio 2012. Ta wersja wymaga również ponownego wygenerowania plików projektu UnityVS.

## <a name="1060---internal-build"></a>1.0.6.0 — kompilacja wewnętrzna
Wydanie 12 września 2012

## <a name="1050"></a>1.0.5.0

Wydanie 10 września 2012

### <a name="bug-fixes"></a>Poprawki błędów

- Stała generacja plików projektu, gdy skrypty lub cieniowanie mają nieprawidłowy znak XML.

- Stałe wykrywanie wystąpień aparatu Unity, gdy środowisko Unity zostało połączone z serwerem zasobów. Wyzwolone błędy otwierania plików z aparatu Unity i automatycznego połączenia debugera programu Visual Studio.

## <a name="1040"></a>1.0.4.0

Wydanie 5 września 2012

### <a name="new-features"></a>Nowe funkcje

- Automatyczna konwersja symboli debugowania w środowisku Unity.

    Jeśli masz zestaw .NET. dll ze skojarzonym z nim plikiem. pdb w folderze Asset, po prostu zaimportuj zestaw i UnityVS przekonwertujemy plik. pdb do pliku symboli debugowania, który jest rozpoznawany przez aparat skryptów aparatu Unity, i będzie można przejść do zestawów .NET z UnityVS.

### <a name="bug-fixes"></a>Poprawki błędów

- Stała awaria UnityVS podczas debugowania spowodowana przez wyjątki zgłoszone przez metody lub właściwości wewnątrz aparatu Unity.

## <a name="1030"></a>1.0.3.0

Wydanie 4 września 2012

### <a name="new-features"></a>Nowe funkcje

- Nowa opcja konfiguracji, aby wyłączyć użycie UnityVS do otwierania plików z aparatu Unity.

### <a name="bug-fixes"></a>Poprawki błędów

- Stałe generowanie odwołań do UnityEditor dla projektów bez edytora.

- Stała definicja symbolu UNITY_EDITOR dla projektów nie będących edytorami.

- Naprawiono losowy program VS Crash z powodu niestandardowego paska stanu.

## <a name="1020"></a>1.0.2.0

Wydanie 30 sierpnia 2012

### <a name="bug-fixes"></a>Poprawki błędów

- Rozwiązano konflikt z debugerem PythonTools.

- Stałe odwołania do mono. Cecil.

- Rozwiązano problem polegający na tym, jak zestawy skryptów zostały pobrane z aparatu Unity z aparatu Unity 4 B7.

## <a name="1010"></a>1.0.1.0

Wydana 28 sierpnia 2012

### <a name="new-features"></a>Nowe funkcje

- Obsługa wersji zapoznawczej dla aparatu Unity 4,0 beta.

### <a name="bug-fixes"></a>Poprawki błędów

- Naprawiono inspekcję właściwości zgłaszających wyjątki.

- Naprawiono malejąco na podstawie obiektów podstawowych podczas przeprowadzania inspekcji obiektów.

- Usunięto pustą listę rozwijaną dla punktu wstawiania w Kreatorze działania.

- Naprawiono uzupełnianie dla biblioteki DLL wewnątrz folderu zasobów dla UnityScript i boo.

## <a name="1000---initial-release"></a>1.0.0.0 — wersja początkowa
Opublikowano 22 sierpnia 2012
