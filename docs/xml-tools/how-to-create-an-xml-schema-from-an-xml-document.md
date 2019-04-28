---
title: Tworzenie schematu XML
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e93155f230ee4a564116f5d1357a97923706c36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783496"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Instrukcje: Tworzenie schematu XML na podstawie dokumentu XML

Edytor XML umożliwia tworzenie schematu języka (XSD) definicji schematu XML z dokumentu XML. Określa plik XML, jak schemat jest generowany w następujący sposób:

- Jeśli dokument XML ma schemat lub definicji typu dokumentu (DTD) skojarzonych z nim, dane w dokumencie XML umożliwia wywnioskować nowego schematu XML.

- Jeśli dokument XML zawiera skojarzone DTD, zewnętrznej definicji DTD i wewnętrzny podzbiór są konwertowane na odpowiedni schemat XML.

- Jeśli dokument XML zawiera wbudowany schemat danych XML (XDR), schemat XDR jest konwertowany na odpowiedni schemat XML.

Schematów, które są tworzone są następnie używane w celu zapewnienia funkcji IntelliSense dla pliku XML.

Aby uzyskać więcej informacji na temat aparatu wnioskowania schematu, zobacz [wnioskowanie schematu XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Aby utworzyć schemat XML

1. Otwórz plik XML w programie Visual Studio.

2. Na pasku menu wybierz **XML** > **Create Schema**.

   Dokument schematu XML, zostanie utworzony i otwarty dla każdej przestrzeni nazw w pliku XML. Każdy schematu zostanie otwarty jako inny plik tymczasowy. Schematy mogą być zapisywane na dysku, dodane do projektu lub odrzucone.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)