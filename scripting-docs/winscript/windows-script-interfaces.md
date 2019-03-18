---
title: Interfejsy skryptów Windows | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4c750627-6797-4857-9f5e-e5f54371f83c
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: acb62f3dc5774ef8574fded3c0537e97611049c2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58154429"
---
# <a name="windows-script-interfaces"></a>Interfejsy skryptów systemu Windows

Interfejsy skryptów systemu Microsoft Windows umożliwiają aplikację w celu dodania skryptów i automatyzacji OLE. Hosty, które zależą od skryptów Windows Scripting umożliwia aparatów obsługi skryptów z wielu źródeł i dostawców Zarządzanie skryptów między składnikami. Implementacja sam skrypt — język, składni, trwałym formacie, model wykonywania i tak dalej — pozostało do dostawcy skryptu.

Dokumentacja skryptów Windows jest podzielona na następujące sekcje:

[Hosty skryptów systemu Windows](../winscript/windows-script-hosts.md)

[Aparaty skryptów systemu Windows](../winscript/windows-script-engines.md)

[Przegląd debugowania aktywnego skryptu](../winscript/active-script-debugging-overview.md)

[Przegląd profilowania aktywnego skryptu](../winscript/active-script-profiling-overview.md)

[Dokumentacja interfejsów skryptów systemu Windows](../winscript/reference/windows-script-interfaces-reference.md)

## <a name="windows-script-background"></a>Tło skrypt Windows

Interfejsy skryptów Windows można podzielić na dwie kategorie: Hosty skryptów Windows i aparatów skryptów Windows. Host tworzy silnik wykonywania skryptów i wywołuje na aparacie na uruchamianie skryptów. Hosty skryptów Windows należą:

- Microsoft Internet Explorer

- Narzędzia do tworzenia internetowego

- Powłoka

Aparaty skryptów Windows mogą być tworzone dla dowolnego języka lub środowiska wykonawczego, w tym:

- Microsoft Visual Basic Scripting Edition (VBScript)

- Perl

- Lisp

Do wdrożenia hosta był jak najbardziej elastyczny, otoka automatyzacji OLE dla skryptu Windows jest dostarczany. Hosta, który używa tego obiektu otoki do utworzenia wystąpienia silnika wykonywania skryptów nie ma jednak stopnia kontroli nad przestrzeń nazw czasu wykonywania, stan trwały modelu i tak dalej, która będzie używać skryptów Windows bezpośrednio.

Projekt skryptu Windows izoluje elementy interfejsu wymagane tylko w środowisku tworzenia pakietów administracyjnych, aby nonauthoring hostów (takie jak przeglądarki i przeglądarki) i aparatów skryptów (np. VBScript) mogą być przechowywane uproszczone.

## <a name="windows-script-basic-architecture"></a>Podstawowa architektura skrypt Windows

Poniższa ilustracja przedstawia interakcję między hostem skryptów Windows i aparat skryptów Windows.

Kroki związane z interakcji między hostem i aparat są podane w poniższej liście.

1.  Utwórz projekt. Host ładuje projektu lub dokumentu. (Ten krok nie jest na Windows skryptu, ale został tu zawarty, aby informacje były kompletne).

2.  Utwórz aparat skryptu Windows. Wywołania hosta `CoCreateInstance` Aby utworzyć nowy aparat skryptu Windows, określając identyfikator klasy (CLSID) z konkretnego aparatu skryptów do użycia. Na przykład przeglądarki HTML programu Internet Explorer otrzymuje identyfikator klasy silnik wykonywania skryptów za pomocą identyfikatora CLSID = atrybutu HTML \<obiektu > tag.

3.  Ładowanie skryptu przez. Jeśli zawartość skryptu zostały utrwalone, host, wywołuje aparat skryptu `IPersist*::Load` metoda ze źródłem danych, jej skrypt zbioru storage, stream lub właściwość. W przeciwnym razie host używa `IPersist*::InitNew` lub [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) metodę, aby utworzyć skrypt o wartości null. Host, który przechowuje skrypt jako tekst, można używać [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) ze źródłem danych silnik wykonywania skryptów tekst skryptu, po wywołaniu `IActiveScriptParse::InitNew`.

4.  Dodaj elementy o nazwie. Dla każdego najwyższego poziomu o nazwie elementu (na przykład stron i formularzy) zaimportowane do przestrzeni nazw aparatu skryptów, wywołuje hosta [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md) metodę, aby utworzyć wpis w przestrzeni nazw aparatu. Ten krok nie jest konieczne, jeśli elementy najwyższego poziomu o nazwie są już częścią trwały stan skryptu załadowane w kroku 3. Host nie używa `IActiveScript::AddNamedItem` dodać podpoziomu o nazwie elementy (takie jak formanty na stronie HTML); zamiast aparat pośrednio uzyskuje dostęp do elementów podpoziomu z elementów najwyższego poziomu za pomocą hosta `ITypeInfo` i `IDispatch` interfejsów.

5.  Uruchom skrypt. Host powoduje, że aparat rozpocząć uruchamianie skryptu przez ustawienie flagi SCRIPTSTATE_CONNECTED w [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) metody. To wywołanie prawdopodobnie wykona wszelkich skryptów aparatu konstrukcji pracy, w tym statyczne powiązania, Podłączanie do zdarzeń (patrz poniżej) i wykonywanie kodu, w sposób podobny do inicjowanych przez skrypty `main()` funkcji.

6.  Uzyskaj informacje o elementach. Każdorazowo, aparat skryptu musi skojarzyć symbolu z elementem najwyższego poziomu wywoływanych przez nią [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md) metody, która zwraca informacje na temat danego elementu.

7.  Podpinanie zdarzeń. Przed uruchomieniem skryptu rzeczywiste, aparat skryptów łączy się z zdarzeń z odpowiednich obiektów za pomocą `IConnectionPoint` interfejsu.

8.  Wywoływanie właściwości i metody. Po uruchomieniu skryptu, aparat skryptów potrafi rozpoznać odwołania do metod i właściwości na nazwane obiekty za pośrednictwem `IDispatch::Invoke` lub innych standardowych mechanizmów powiązania OLE.

## <a name="windows-script-terms"></a>Warunki skrypt Windows

Ta lista zawiera definicje terminów związanych z obsługi skryptów, używane w tym dokumencie.

|Termin|Definicja|
|----------|----------------|
|Kod obiektu|Wystąpienia utworzone przez silnik wykonywania skryptów, który jest skojarzony z elementem nazwanych, takim jak modułu formularza w języku Visual Basic lub skojarzone z elementem o nazwie klasy języka C++. Najlepiej jest obiekt OLE Component Object Model (COM), który obsługuje automatyzacji OLE, więc hosta lub inny organ-script można manipulować obiektu kodu.|
|Element o nazwie|Obiekt OLE COM (najlepiej obsługującej automatyzacji OLE), hosta jeśli uzna, że interesujące do skryptu. Przykłady obejmują strony HTML i przeglądarki w przeglądarce sieci Web i dokumentów i okien dialogowych w programie Microsoft Word.|
|Skrypt|Dane, które tworzą program uruchamiany przez silnik wykonywania skryptów. Skrypt może być ciągłe danych pliku wykonywalnego, tym fragmentów tekstu, bloki konstrukcyjne `pcode`, a nawet kody bajt pliku wykonywalnego specyficzny dla komputera. Host ładuje skrypt do silnika wykonywania skryptów za pomocą jednego z `IPersist*` interfejsy lub za pomocą [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) interfejsu.|
|Silnik wykonywania skryptów|Obiekt OLE, który przetwarza skryptów. Implementuje silnik wykonywania skryptów [IActiveScript](../winscript/reference/iactivescript.md) i, opcjonalnie, [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) interfejsów.|
|Host skryptów|Aplikacja lub program, który jest właścicielem aparat skryptu Windows. Implementuje hosta [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) i, opcjonalnie, [IActiveScriptSiteWindow](../winscript/reference/iactivescriptsitewindow.md) interfejsów.|
|Scriptlet|Część skryptu, który jest dołączany do obiektu za pomocą [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) interfejsu. Kolekcja agregacji skryptlety jest skrypt.|
|Język skryptów|Język, w którym skrypt jest napisane (VBScript, na przykład) i semantyka tego języka.|