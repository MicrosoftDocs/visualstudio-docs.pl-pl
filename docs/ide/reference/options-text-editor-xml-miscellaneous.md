---
title: Opcje, Edytor tekstu, XML, Różne
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: dd468945b1ab9ac83b219b9c8c396f017065e2be
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568129"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Opcje, Edytor tekstu, XML, Różne

Strona **Różne** opcje służy do zmiany ustawień autouzupełniania i schematu edytora XML. Aby uzyskać dostęp do różnych opcji XML, wybierz pozycję **Opcje** > **narzędzi** > **Edytor** > tekstu**XML**, a następnie wybierz pozycję **Różne**.

## <a name="auto-insert"></a>Automatyczne wstawianie

**Zamykanie tagów**

Edytor tekstu dodaje znaczniki zamknięcia podczas tworzenia elementów XML. Jeśli zaznaczony jest tag początkowy elementu, edytor wstawia pasujący tag zamknięcia, w tym pasujący prefiks obszaru nazw. To pole wyboru jest zaznaczone domyślnie.

**Cudzysłowy atrybutów**

Podczas tworzenia atrybutów XML edytor `="` wstawia znaki i `"` umieszcza**^** cieszkę ( ) wewnątrz cudzysłowów. To pole wyboru jest zaznaczone domyślnie.

**Deklaracje obszaru nazw**

Edytor automatycznie wstawia deklaracje obszaru nazw wszędzie tam, gdzie są potrzebne. To pole wyboru jest zaznaczone domyślnie.

**Inne znaczniki (Komentarze, CDATA)**

Komentarze, CDATA, DOCTYPE, instrukcje przetwarzania i inne znaczniki są automatycznie uzupełniane. To pole wyboru jest zaznaczone domyślnie.

## <a name="network"></a>Network (Sieć)

**Automatyczne pobieranie DTD i schematów**

Schematy i definicje typów dokumentów (DTD) są automatycznie pobierane z lokalizacji HTTP. Ta funkcja wykorzystuje System.Net z włączonym wykrywaniem serwera autoproxy. To pole wyboru jest zaznaczone domyślnie.

## <a name="outlining"></a>Tworzenie konspektu

**Wprowadzanie trybu tworzenia po otwarciu plików**

Włącza funkcję tworzenia przekreślenia po otwarciu pliku. To pole wyboru jest zaznaczone domyślnie.

## <a name="caching"></a>Buforowanie

**Schematy**

Określa lokalizację pamięci podręcznej schematu. Przycisk **Przeglądaj** otwiera bieżącą lokalizację pamięci podręcznej schematu w nowym oknie. Domyślną lokalizacją jest *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Zobacz też

- [Opcje XML — formatowanie](options-text-editor-xml-formatting.md)
- [Narzędzia XML w Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
