---
title: 'Instrukcje: Tworzenie schematu XML na podstawie dokumentu XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 59e99320b122424e40da64b530bfe9a84a93eae1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670929"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Instrukcje: Tworzenie schematu XML na podstawie dokumentu XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor XML pozwala utworzyć schemat języka XSD (XML Schema Definition Language) z dokumentu XML. Dokument wystąpienia XML określa sposób generowania schematu w następujący sposób:

- Jeśli dokument XML nie ma skojarzonej ze schematem lub definicją typu dokumentu (DTD), dane w dokumencie XML są używane do wywnioskowania nowego schematu XML.

- Jeśli dokument XML zawiera skojarzony DTD, zewnętrzna definicja DTD i podzbiór wewnętrzny są konwertowane do odpowiedniego schematu XML.

- Jeśli dokument XML zawiera wbudowany schemat danych XML (XDR), schemat XDR jest konwertowany na odpowiedni schemat XML.

  Tworzone schematy są następnie używane do udostępniania funkcji IntelliSense dla dokumentu XML.

  Aby uzyskać więcej informacji o aparacie wnioskowania schematu, zobacz [wnioskowanie schematu XML](https://msdn.microsoft.com/library/b18e7ffd-3c04-482d-9934-ba2f6a59b2c9).

### <a name="to-create-an-xml-schema"></a>Aby utworzyć schemat XML

1. Załaduj dokument wystąpienia XML do edytora XML.

2. Kliknij przycisk **Utwórz schemat** na **pasku narzędzi**.

     Dokument schematu XML jest tworzony i otwierany dla każdej przestrzeni nazw, która znajduje się w dokumencie wystąpienia XML. Każdy schemat jest otwierany jako plik tymczasowy.

     Schematy mogą być zapisywane na dysku, dodawane do projektu lub odrzucane.

    > [!NOTE]
    > Polecenie **Utwórz schemat** jest również dostępne w menu skrótów edytora XML i w menu **XML** .

## <a name="see-also"></a>Zobacz też
 [Edytor XML](../xml-tools/xml-editor.md)
