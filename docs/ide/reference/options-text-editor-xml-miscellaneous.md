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
ms.openlocfilehash: d3421580251a6a871adba311fd609e881e088ebd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969218"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Opcje, Edytor tekstu, XML, różne

Użyj **różne** Strona opcji, aby zmienić ustawienia automatycznego uzupełniania i schematu edytora XML. Aby uzyskać dostęp do różnych opcji XML, wybierz opcję **narzędzia** > **opcje** > **edytora tekstów** > **XML**, a następnie wybierz **różne**.

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

Określa lokalizację pamięci podręcznej schematów. **Przeglądaj** przycisk otwiera bieżącej lokalizacji pamięci podręcznej schematu w nowym oknie. Domyślna lokalizacja to *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Zobacz także

- [Opcje XML — formatowanie](options-text-editor-xml-formatting.md)
- [Narzędzia XML w programie Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)