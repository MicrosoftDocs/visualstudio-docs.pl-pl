---
title: Tworzenie schematu XML
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 73563d732aab48192892794c15750bc9e5d3eb6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645961"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Instrukcje: Tworzenie schematu XML na podstawie dokumentu XML

Edytor XML pozwala utworzyć schemat języka XSD (XML Schema Definition Language) z dokumentu XML. Plik XML określa sposób generowania schematu w następujący sposób:

- Jeśli dokument XML nie ma skojarzonej ze schematem lub definicją typu dokumentu (DTD), dane w dokumencie XML są używane do wywnioskowania nowego schematu XML.

- Jeśli dokument XML zawiera skojarzony DTD, zewnętrzna definicja DTD i podzbiór wewnętrzny są konwertowane do odpowiedniego schematu XML.

- Jeśli dokument XML zawiera wbudowany schemat danych XML (XDR), schemat XDR jest konwertowany na odpowiedni schemat XML.

Tworzone schematy są następnie używane do udostępniania funkcji IntelliSense dla pliku XML.

Aby uzyskać więcej informacji o aparacie wnioskowania schematu, zobacz artykuł [wnioskowanie schematu XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Aby utworzyć schemat XML

1. Otwórz plik XML w programie Visual Studio.

2. Na pasku menu wybierz pozycję **XML**  > **Utwórz schemat**.

   Dokument schematu XML zostanie utworzony i otwarty dla każdej przestrzeni nazw znalezionej w pliku XML. Każdy schemat jest otwierany jako plik tymczasowy. Schematy mogą być zapisywane na dysku, dodawane do projektu lub odrzucane.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)