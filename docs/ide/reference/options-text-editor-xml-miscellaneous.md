---
title: Opcje, Edytor tekstu, XML, różne
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fed24e39b29907784d6101f7871f7a292850c457
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389360"
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

- [Porady: tworzenie dokumentacji XML (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/how-to-create-xml-documentation)
- [Generowanie kodu](../code-generation-in-visual-studio.md)