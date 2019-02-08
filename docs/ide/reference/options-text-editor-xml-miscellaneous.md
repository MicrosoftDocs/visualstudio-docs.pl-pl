---
title: Opcje, Edytor tekstu, XML, różne
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4300eaa751eb8ac24461f9aca11e75c07d78a94d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930288"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Opcje, Edytor tekstu, XML, różne

Użyj **różne** strony właściwości, aby zmienić ustawienia automatycznego uzupełniania i schematu edytora XML. Aby otworzyć **opcje** okno dialogowe, kliknij przycisk **narzędzia** menu, a następnie kliknij przycisk **opcje**. Aby uzyskać dostęp do **różne** właściwości rozwiń **edytora tekstów** > **XML** > **różne**węzła.

## <a name="auto-insert"></a>Automatyczne wstawianie

**Zamknij tagów**

Podczas tworzenia elementów XML, Edytor tekstu dodaje Zamknij tagów. Jeśli tagu początkowym elementu jest zaznaczone, Edytor wstawia pasującego tagu Zamknij, łącznie z dopasowania prefiksu przestrzeni nazw. To pole wyboru jest zaznaczone domyślnie.

**Cudzysłowy atrybutu**

Podczas tworzenia atrybutów XML, Edytor wstawia `="` i `"` znaków i określa położenie karetki (**^**) wewnątrz cudzysłowów. To pole wyboru jest zaznaczone domyślnie.

**Deklaracji Namespace**

Edytor automatycznie wstawi deklaracje przestrzeni nazw, wszędzie tam, gdzie jest to konieczne. To pole wyboru jest zaznaczone domyślnie.

**Innych znaczników (komentarze, CDATA)**

Komentarze, CDATA, elementu DOCTYPE, instrukcje przetwarzania i innych znaczników jest Autouzupełniania. To pole wyboru jest zaznaczone domyślnie.

## <a name="network"></a>Sieć

**Automatycznie pobieraj definicje DTD i schematy**

Schematy i definicji typu dokumentu (pliki DTD) są automatycznie pobierane z lokalizacji HTTP. Ta funkcja używa przestrzeni nazw System.Net z włączone wykrywanie serwerów autoproxy. To pole wyboru jest zaznaczone domyślnie.

## <a name="outlining"></a>Tworzenie konspektu

**Przejdź do trybu konspektu po otwarciu plików**

Włącza funkcję tworzenia konspektów podczas otwierania pliku. To pole wyboru jest zaznaczone domyślnie.

## <a name="caching"></a>Buforowanie

**Schematy**

Określa lokalizację pamięci podręcznej schematów. Przycisk przeglądania (...) w nowym oknie zostanie otwarta bieżącej lokalizacji pamięci podręcznej schematu. Domyślna lokalizacja to  *\<Management Studio katalog_instalacji >* \Xml\Schemas.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie dokumentacji XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Generowanie kodu](../code-generation-in-visual-studio.md)