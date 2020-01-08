---
title: Opcje, Edytor tekstu, XML, różne
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: dd468945b1ab9ac83b219b9c8c396f017065e2be
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568129"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Opcje, Edytor tekstu, XML, różne

Na stronie **różne** opcje można zmienić ustawienia autouzupełniania i schematu dla edytora XML. Aby uzyskać dostęp do różnych opcji XML, wybierz **narzędzia** > **Opcje** > **edytorze tekstów** > **XML**, a następnie wybierz **różne**.

## <a name="auto-insert"></a>Autowstawianie

**Zamknij Tagi**

Edytor tekstu dodaje tagi zamykające podczas tworzenia elementów XML. Jeśli wybrano tag początkowy elementu, Edytor wstawia pasujący tag zamykający, w tym pasujący prefiks przestrzeni nazw. To pole wyboru jest domyślnie zaznaczone.

**Cudzysłowy atrybutów**

Podczas tworzenia atrybutów XML edytor wstawia `="` i `"` znaków oraz umieszcza karetkę ( **^** ) wewnątrz znaków cudzysłowu. To pole wyboru jest domyślnie zaznaczone.

**Deklaracje przestrzeni nazw**

Edytor automatycznie wstawia deklaracje przestrzeni nazw wszędzie tam, gdzie są one zbędne. To pole wyboru jest domyślnie zaznaczone.

**Inne znaczniki (komentarze, CDATA)**

Komentarze, CDATA, DOCTYPE, instrukcje przetwarzania i inne znaczniki są autouzupełniane. To pole wyboru jest domyślnie zaznaczone.

## <a name="network"></a>Sieć

**Automatycznie pobieraj definicje DTD i schematy**

Schematy i definicje typu dokumentu (DTD) są automatycznie pobierane z lokalizacji HTTP. Ta funkcja używa System.Net z włączonym wykrywaniem serwera AutoProxy. To pole wyboru jest domyślnie zaznaczone.

## <a name="outlining"></a>Tworzenie konspektu

**Wejdź do trybu konspektu przy otwieraniu plików**

Włącza funkcję tworzenia konspektu, gdy plik zostanie otwarty. To pole wyboru jest domyślnie zaznaczone.

## <a name="caching"></a>Buforowanie

**Punktu**

Określa lokalizację pamięci podręcznej schematu. Przycisk **Przeglądaj** otwiera bieżącą lokalizację pamięci podręcznej schematu w nowym oknie. Domyślna lokalizacja to *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Zobacz także

- [Opcje XML — formatowanie](options-text-editor-xml-formatting.md)
- [Narzędzia XML w programie Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
