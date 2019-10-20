---
title: Właściwości dokumentu XML, okno właściwości | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f620cc2bd189dccf067c6276f760d21cde5cf05e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669516"
---
# <a name="xml-document-properties-properties-window"></a>Właściwości dokumentu XML, Właściwości, okno
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **Właściwości** zawiera podstawowe informacje o dokumencie aktywnym w edytorze XML. Dostępne właściwości różnią się w zależności od typu dokumentu XML, który jest obecnie aktywny.

> [!NOTE]
> Wszystkie właściwości dokumentu XML są zapisywane w rozwiązaniu. W związku z tym nie trzeba ponownie wprowadzać tych wartości przy następnym otwarciu rozwiązania.

 **Kodowanie** Kodowanie znaków dla pliku. Zmiana tej właściwości powoduje także zmianę atrybutu kodowania w deklaracji XML i odwrotnie. Nowe kodowanie będzie używane do kodowania pliku podczas zapisywania pliku.

 **Dane wejściowe** Dokument wejściowy skojarzony z arkuszem stylów XSLT. Jest on używany przez polecenie **ShowXSLT Output** . Dokument można wybrać za pomocą przycisku Przeglądaj (.. **.** ).

 Ta właściwość jest widoczna tylko wtedy, gdy plik XSLT jest obecnie aktywny w oknie edytora.

 **Dane wyjściowe** Plik, który jest generowany podczas przekształcania dokumentu XML.

 Jeśli plik nie zostanie określony, domyślna nazwa pliku jest generowana na podstawie atrybutu `method` w elemencie `xsl:output`, który określa rozszerzenie pliku. Plik domyślny znajduje się w katalogu tymczasowym bieżącego użytkownika.

 **Schematy** Schematy do użycia na potrzeby walidacji. Przycisk otwiera okno dialogowe **schematy XSD** , za pomocą którego można wybrać schematy do użycia.

 Możesz również wprowadzić ścieżkę do schematów. Jeśli określono wiele schematów, każda ścieżka schematu musi być ujęta w cudzysłów.

 **Arkusz stylów** Plik XSLT, który jest używany do przekształcania dokumentu, gdy jest używane polecenie **Pokaż dane wyjściowe XSLT** . Jeśli to pole jest puste, gdy używane jest polecenie **Pokaż dane wyjściowe XSLT** , Edytor używa wartości podanej w instrukcji przetwarzania `xml-stylesheet` dokumentu lub wyświetla komunikat o nazwie pliku.

 Podczas edytowania pliku XSLT ta właściwość może służyć do określenia, że inny arkusz stylów ma być używany, gdy jest zaznaczone polecenie **Pokaż dane wyjściowe XSLT** lub **Debuguj XSLT** . Na przykład możesz to zrobić podczas edytowania arkusza stylów, który znajduje się w nadrzędnym arkuszu stylów.

## <a name="see-also"></a>Zobacz też
 [](../xml-tools/xml-editor.md) [Składniki edytora XML](../xml-tools/xml-editor-components.md) edytora XML
