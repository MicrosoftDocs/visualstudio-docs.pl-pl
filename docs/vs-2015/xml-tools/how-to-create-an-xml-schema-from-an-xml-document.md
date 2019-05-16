---
title: 'Instrukcje: Tworzenie schematu XML z dokumentu XML | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a732f0c6a9758de3ebd918559203b13a56d6a0ae
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697787"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Instrukcje: Tworzenie schematu XML na podstawie dokumentu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor XML służy do tworzenia schematu języka (XSD) definicji schematu XML z dokumentu XML. Wystąpienia dokumentu XML określa, jak wygenerować schematu, w następujący sposób:  
  
- Jeśli dokument XML ma schemat lub definicji typu dokumentu (DTD) skojarzonych z nim, dane w dokumencie XML umożliwia wywnioskować nowego schematu XML.  
  
- Jeśli dokument XML zawiera skojarzone DTD, zewnętrznej definicji DTD i wewnętrzny podzbiór są konwertowane na odpowiedni schemat XML.  
  
- Jeśli dokument XML zawiera wbudowany schemat danych XML (XDR), schemat XDR jest konwertowany na odpowiedni schemat XML.  
  
  Schematy, które są tworzone są następnie używane do udostępni funkcję IntelliSense dla dokumentu XML.  
  
  Aby uzyskać więcej informacji na temat aparatu wnioskowania schematu, zobacz [wnioskowanie schematu XML](https://msdn.microsoft.com/library/b18e7ffd-3c04-482d-9934-ba2f6a59b2c9).  
  
### <a name="to-create-an-xml-schema"></a>Aby utworzyć schemat XML  
  
1. Ładowanie wystąpienia dokumentu XML w edytorze XML.  
  
2. Kliknij przycisk **Create Schema** przycisk **narzędzi**.  
  
     Dokument schematu XML, zostanie utworzony i otwarty dla każdej przestrzeni nazw w dokumencie wystąpienia XML. Każdy schematu zostanie otwarty jako inny plik tymczasowy.  
  
     Schematy mogą być zapisywane na dysku, dodane do projektu lub odrzucone.  
  
    > [!NOTE]
    > **Create Schema** polecenia jest także dostępny z menu kontekstowego edytora XML i w obszarze **XML** menu.  
  
## <a name="see-also"></a>Zobacz też  
 [Edytor XML](../xml-tools/xml-editor.md)
