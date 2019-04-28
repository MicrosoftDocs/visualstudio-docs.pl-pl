---
title: Właściwości dokumentu XML, Właściwości, okno
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 679ac529708a49d18025672ce8f880c4f7710471
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808135"
---
# <a name="xml-document-properties-properties-window"></a>Właściwości dokumentu XML, okno właściwości

**Właściwości** okno zawiera podstawowe informacje o dokument, który jest aktywny w edytorze XML. Właściwości, które są dostępne, różnią się w zależności od typu dokumentu XML, który jest obecnie aktywny.

> [!NOTE]
> Wszystkie właściwości dokumentu XML są zapisywane w rozwiązaniu. W rezultacie jest konieczne ponowne wprowadzenie tych wartości, przy następnym otwarciu rozwiązania.

**Kodowanie**

Kodowanie znaków dla pliku. Zmienianie tej właściwości również zmiany kodowanie atrybutu w deklaracji XML i odwrotnie. Nowe kodowanie jest używany do kodowania pliku, podczas zapisywania pliku.

**Dane wejściowe**

Dokument wejściowy skojarzone z arkusza stylów XSLT. Jest on używany przez **Start XSLT** polecenia, na przykład **XML** > **Rozpocznij debugowanie kodu XSLT bez**. Dokumentu można wybrać za pomocą przeglądania (**...** ) przycisku.

Ta właściwość jest widoczny tylko wtedy, gdy plik XSLT jest otwarty w edytorze.

**Output**

Plik, który jest generowany, gdy Przekształcenie dokumentu XML.

Jeśli plik nie zostanie określony, domyślna nazwa pliku jest generowany na podstawie `method` atrybutu na `xsl:output` element, który określa rozszerzenie pliku. Domyślny plik znajduje się w katalogu tymczasowym bieżącego użytkownika.

**Schematy**

Schematy do użycia w celu weryfikacji. Ten przycisk otwiera **schematy XSD** okno dialogowe, które mogą służyć do wybierania schematy do użycia.

Można również wprowadzić ścieżkę, do schematów. Jeśli nie określono wiele schematów, każda ścieżka schematu muszą być ujęte w cudzysłów.

**Arkusz stylów**

Plik XSLT, która jest używana do przekształcania dokumentu po **Rozpocznij debugowanie kodu XSLT** i **Rozpocznij debugowanie kodu XSLT bez** polecenia łącza są używane. Jeśli to pole jest puste, Edytor używa wartość podana w `xml-stylesheet` przetwarzania instrukcji, dokumentu lub jego wyświetli monit o podanie nazwy pliku.

Podczas edytowania pliku XSLT, ta właściwość może służyć do określenia, że arkusz stylów różnych powinny być używane podczas **Rozpocznij debugowanie kodu XSLT** lub **Rozpocznij debugowanie kodu XSLT bez** polecenie jest zaznaczone. Na przykład można to zrobić podczas edytowania arkusza stylów, który znajduje się w arkuszu stylów nadrzędnej.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)