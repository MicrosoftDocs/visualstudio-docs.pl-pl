---
title: Właściwości dokumentu XML, okno właściwości | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7906cc40eef813fcfd8996954e7073eb3e8508e1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438856"
---
# <a name="xml-document-properties-properties-window"></a>Właściwości dokumentu XML, Właściwości, okno
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Właściwości** okno zawiera podstawowe informacje o dokument, który jest aktywny w edytorze XML. Właściwości, które są dostępne, różnią się w zależności od typu dokumentu XML, który jest obecnie aktywny.  
  
> [!NOTE]
> Wszystkie właściwości dokumentu XML są zapisywane w rozwiązaniu. W rezultacie jest konieczne ponowne wprowadzenie tych wartości, przy następnym otwarciu rozwiązania.  
  
 **Kodowanie**  
 Kodowanie znaków dla pliku. Zmienianie tej właściwości również zmiany kodowanie atrybutu w deklaracji XML i odwrotnie. Nowe kodowanie będzie służyć do kodowania pliku, podczas zapisywania pliku.  
  
 **Dane wejściowe**  
 Dokument wejściowy skojarzone z arkusza stylów XSLT. Jest on używany przez **dane wyjściowe ShowXSLT** polecenia. Dokumentu można wybrać za pomocą przeglądania (**...** ) przycisku.  
  
 Ta właściwość jest widoczny tylko wtedy, gdy plik XSLT jest aktywna, w oknie edytora.  
  
 **Output**  
 Plik, który jest generowany, gdy Przekształcenie dokumentu XML.  
  
 Jeśli plik nie zostanie określony, domyślna nazwa pliku jest generowany na podstawie `method` atrybutu na `xsl:output` element, który określa rozszerzenie pliku. Domyślny plik znajduje się w katalogu tymczasowym bieżącego użytkownika.  
  
 **Schematy**  
 Schematy do użycia w celu weryfikacji. Ten przycisk otwiera **schematy XSD** okno dialogowe, które mogą służyć do wybierania schematy do użycia.  
  
 Można również wprowadzić ścieżkę, do schematów. Jeśli nie określono wiele schematów, każda ścieżka schematu muszą być ujęte w cudzysłów.  
  
 **Arkusz stylów**  
 Plik XSLT, która jest używana do przekształcania dokumentu po **Pokaż dane wyjściowe XSLT** polecenie jest używane. Jeśli to pole jest puste w przypadku **Pokaż dane wyjściowe XSLT** polecenie jest używane, Edytor używa wartość podana w `xml-stylesheet` przetwarzania instrukcji dokument, lub wyświetli monit o podanie nazwy pliku.  
  
 Podczas edytowania pliku XSLT, ta właściwość może służyć do określenia, że arkusz stylów różnych powinny być używane podczas **Pokaż dane wyjściowe XSLT** lub **debugowania XSLT** polecenie jest zaznaczone. Na przykład można to zrobić, edytując arkusza stylów, który znajduje się w arkuszu stylów nadrzędnej.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor XML](../xml-tools/xml-editor.md)   
 [Składniki edytora XML](../xml-tools/xml-editor-components.md)
