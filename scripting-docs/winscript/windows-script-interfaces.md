---
title: Interfejsy skryptów systemu Windows | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 141f3f0e60e797a4104c3e276775631f6e9196c5
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835410"
---
# <a name="windows-script-interfaces"></a>Interfejsy skryptów systemu Windows

Interfejsy skryptów systemu Microsoft Windows umożliwiają aplikacji Dodawanie skryptów i automatyzacji OLE. Hosty obsługujące skrypty, które opierają się na skrypcie systemu Windows, mogą używać aparatów skryptów z wielu źródeł i dostawców do zarządzania skryptami między składnikami. Implementacja samego skryptu — język, składnia, format trwały, model wykonywania i tak dalej — jest pozostawiony do dostawcy skryptów.

Dokumentacja skryptów systemu Windows jest podzielona na następujące sekcje:

[Hosty skryptów systemu Windows](../winscript/windows-script-hosts.md)

[Aparaty skryptów systemu Windows](../winscript/windows-script-engines.md)

[Przegląd debugowania aktywnego skryptu](../winscript/active-script-debugging-overview.md)

[Przegląd profilowania aktywnego skryptu](../winscript/active-script-profiling-overview.md)

[Dokumentacja interfejsów skryptów systemu Windows](../winscript/reference/windows-script-interfaces-reference.md)

## <a name="windows-script-background"></a>Tło skryptu systemu Windows

Interfejsy skryptów systemu Windows dzielą się na dwie kategorie: hosty skryptów systemu Windows i aparaty skryptów systemu Windows. Host tworzy aparat skryptów i wywołuje aparat do uruchamiania skryptów. Przykłady hostów skryptów systemu Windows obejmują:

- Microsoft Internet Explorer

- Narzędzia autorskie Internetu

- Powłoka

Aparaty skryptów systemu Windows można opracować dla dowolnego języka lub środowiska wykonawczego, w tym:

- Microsoft Visual Basic Scripting Edition (VBScript)

- Języku

- Lisp

Aby zapewnić, że implementacja hosta jest możliwie elastyczna, udostępniana jest funkcja otoki automatyzacji OLE dla systemu Windows. Jednak Host używający tego obiektu otoki do tworzenia wystąpienia aparatu skryptów nie ma kontroli nad przestrzenią nazw czasu wykonywania, modelem trwałości i tak dalej, że gdyby używał bezpośrednio skryptu systemu Windows.

Projekt skryptu systemu Windows izoluje elementy interfejsu wymagane tylko w środowisku autorskim, aby hosty nietworzące autorstwa (takie jak przeglądarki i przeglądarki) i aparaty skryptów (na przykład VBScript) mogły być lekkie.

## <a name="windows-script-basic-architecture"></a>Podstawowa architektura skryptów systemu Windows

Poniższa ilustracja przedstawia interakcję między hostem skryptów systemu Windows i aparatem skryptów systemu Windows.

Kroki związane z interakcją między hostem i aparatem są podane na poniższej liście.

1. Utwórz projekt. Host ładuje projekt lub dokument. (Ten krok nie jest szczególny dla skryptu systemu Windows, ale jest tutaj uwzględniony do kompletności).

2. Utwórz aparat skryptów systemu Windows. Host wywołuje `CoCreateInstance` , aby utworzyć nowy aparat skryptów systemu Windows, określając identyfikator klasy (CLSID) określonego aparatu skryptów do użycia. Na przykład przeglądarka HTML programu Internet Explorer otrzymuje identyfikator klasy aparatu skryptów za pomocą atrybutu CLSID = w \<OBJECT> tagu HTML.

3. Załaduj skrypt. Jeśli zawartość skryptu została utrwalona, Host wywołuje metodę aparatu skryptów, `IPersist*::Load` Aby uzyskać strumieniowe źródło danych, strumień lub zbiór właściwości. W przeciwnym razie host używa `IPersist*::InitNew` metody lub [IActiveScriptParse:: InitNew](../winscript/reference/iactivescriptparse-initnew.md) , aby utworzyć skrypt o wartości null. Host, który utrzymuje skrypt jako tekst, może używać [IActiveScriptParse::P arsescripttext](../winscript/reference/iactivescriptparse-parsescripttext.md) do strumieniowego aparatu obsługi skryptów tekstu skryptu po wywołaniu `IActiveScriptParse::InitNew` .

4. Dodaj nazwane elementy. Dla każdego elementu o nazwie najwyższego poziomu (takiego jak strony i formularze) zaimportowanego do obszaru nazw aparatu skryptów, Host wywołuje metodę [IActiveScript:: AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) , aby utworzyć wpis w przestrzeni nazw aparatu. Ten krok nie jest konieczny, jeśli nazwane elementy najwyższego poziomu są już częścią trwałego stanu skryptu załadowanego w kroku 3. Host nie używa `IActiveScript::AddNamedItem` do dodawania elementów o nazwach podpoziomu (takich jak kontrolki na stronie HTML); aparat pośredni pośrednio uzyskuje elementy poziomu z elementów najwyższego poziomu przy użyciu `ITypeInfo` interfejsów hosta i `IDispatch` .

5. Uruchom skrypt. Host powoduje uruchomienie skryptu przez aparat przez ustawienie flagi SCRIPTSTATE_CONNECTED w metodzie [IActiveScript:: SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) . To wywołanie prawdopodobnie wykona wszystkie prace konstrukcyjne aparatu skryptów, w tym powiązania statyczne, podłączając do zdarzeń (patrz poniżej) i wykonując kod, w sposób podobny do funkcji skryptowej `main()` .

6. Pobierz informacje o elemencie. Za każdym razem, gdy aparat skryptów musi skojarzyć symbol z elementem najwyższego poziomu, wywołuje metodę [IActiveScriptSite:: GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) , która zwraca informacje dotyczące danego elementu.

7. Podłącz zdarzenia. Przed uruchomieniem rzeczywistego skryptu aparat skryptów łączy się ze zdarzeniami wszystkich odpowiednich obiektów za pomocą `IConnectionPoint` interfejsu.

8. Wywoływanie właściwości i metod. Po uruchomieniu skryptu aparat skryptów realizuje odwołania do metod i właściwości obiektów nazwanych za pośrednictwem `IDispatch::Invoke` lub innych standardowych mechanizmów powiązań OLE.

## <a name="windows-script-terms"></a>Warunki skryptów systemu Windows

Ta lista zawiera definicje terminów związanych z skryptami używanych w tym dokumencie.

|Termin|Definicja|
|----------|----------------|
|Obiekt kodu|Wystąpienie utworzone przez aparat skryptów, który jest skojarzony z nazwanym elementem, taki jak moduł za formularzem w Visual Basic, lub Klasa C++ skojarzona z nazwanym elementem. Najlepiej jest to obiekt OLE Component Object Model (COM), który obsługuje automatyzację OLE, dzięki czemu Host lub inna jednostka niebędąca skryptami mogą manipulować obiektem kodu.|
|Nazwany element|Obiekt OLE COM (najlepiej obsługujący automatyzację OLE), który jest uważany za interesujący dla skryptu. Przykładami mogą być strony HTML i przeglądarki w przeglądarce internetowej oraz dokumenty i okna dialogowe programu Microsoft Word.|
|Skrypt|Dane, które tworzą program, który jest uruchamiany przez aparat skryptów. Skrypt może być wszelkimi ciągłymi danymi wykonywalnymi, w tym fragmentami tekstu, blokami `pcode` , a nawet kodami bajtów wykonywalnych specyficznych dla maszyn. Host ładuje skrypt do aparatu skryptów za pomocą jednego z `IPersist*` interfejsów lub interfejsu [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) .|
|Aparat skryptów|Obiekt OLE, który przetwarza skrypty. Aparat skryptów implementuje interfejsy [IActiveScript](../winscript/reference/iactivescript.md) i, opcjonalnie, [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) .|
|Host skryptów|Aplikacja lub program, który jest właścicielem aparatu skryptów systemu Windows. Host implementuje interfejsy [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) i, opcjonalnie, [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md) .|
|Scriptlet|Część skryptu, która jest dołączona do obiektu za pomocą interfejsu [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) . Agregowana kolekcja skryptlety jest skryptem.|
|Język skryptu|Język, w którym skrypt jest pisany (na przykład VBScript) i semantyką tego języka.|