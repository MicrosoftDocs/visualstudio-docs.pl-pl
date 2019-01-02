---
title: 'Instrukcje: Tworzenie schematu XML na podstawie dokumentu XML'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 629519a6df8c570ee806ec7360e03f442042b5ba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915208"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Instrukcje: Tworzenie schematu XML z dokumentu XML

Edytor XML służy do tworzenia schematu języka (XSD) definicji schematu XML z dokumentu XML. Wystąpienia dokumentu XML określa, jak wygenerować schematu, w następujący sposób:

-   Jeśli dokument XML ma schemat lub definicji typu dokumentu (DTD) skojarzonych z nim, dane w dokumencie XML umożliwia wywnioskować nowego schematu XML.

-   Jeśli dokument XML zawiera skojarzone DTD, zewnętrznej definicji DTD i wewnętrzny podzbiór są konwertowane na odpowiedni schemat XML.

-   Jeśli dokument XML zawiera wbudowany schemat danych XML (XDR), schemat XDR jest konwertowany na odpowiedni schemat XML.

Schematy, które są tworzone są następnie używane do udostępni funkcję IntelliSense dla dokumentu XML.

Aby uzyskać więcej informacji na temat aparatu wnioskowania schematu, zobacz [wnioskowanie schematu XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Aby utworzyć schemat XML

1.  Ładowanie wystąpienia dokumentu XML w edytorze XML.

2.  Kliknij przycisk **Create Schema** przycisk **narzędzi**.

     Dokument schematu XML, zostanie utworzony i otwarty dla każdej przestrzeni nazw w dokumencie wystąpienia XML. Każdy schematu zostanie otwarty jako inny plik tymczasowy.

     Schematy mogą być zapisywane na dysku, dodane do projektu lub odrzucone.

    > [!NOTE]
    >  **Create Schema** polecenia jest także dostępny z menu kontekstowego edytora XML i w obszarze **XML** menu.

## <a name="see-also"></a>Zobacz także

- [Edytor XML](../xml-tools/xml-editor.md)