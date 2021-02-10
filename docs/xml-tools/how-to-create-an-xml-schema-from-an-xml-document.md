---
title: Tworzenie schematu XML
description: Dowiedz się, w jaki sposób używać edytora XML w programie Visual Studio, aby utworzyć schemat języka definicji schematu XML (XSD) z dokumentu XML.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e33a4add7ebc6a3e323331731f3183d7a0dce26f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970286"
---
# <a name="how-to-create-an-xml-schema-from-an-xml-document"></a>Instrukcje: Tworzenie schematu XML na podstawie dokumentu XML

Edytor XML pozwala utworzyć schemat języka XSD (XML Schema Definition Language) z dokumentu XML. Plik XML określa sposób generowania schematu w następujący sposób:

- Jeśli dokument XML nie ma skojarzonej ze schematem lub definicją typu dokumentu (DTD), dane w dokumencie XML są używane do wywnioskowania nowego schematu XML.

- Jeśli dokument XML zawiera skojarzony DTD, zewnętrzna definicja DTD i podzbiór wewnętrzny są konwertowane do odpowiedniego schematu XML.

- Jeśli dokument XML zawiera wbudowany XML-Data ze zmniejszonym (XDR) schematu, schemat XDR zostanie przekonwertowany na odpowiedni schemat XML.

Tworzone schematy są następnie używane do udostępniania funkcji IntelliSense dla pliku XML.

Aby uzyskać więcej informacji o aparacie wnioskowania schematu, zobacz artykuł [wnioskowanie schematu XML](/dotnet/standard/data/xml/inferring-an-xml-schema).

## <a name="to-create-an-xml-schema"></a>Aby utworzyć schemat XML

1. Otwórz plik XML w programie Visual Studio.

2. Na pasku menu wybierz pozycję **XML**  >  **Utwórz schemat**.

   Dokument schematu XML zostanie utworzony i otwarty dla każdej przestrzeni nazw znalezionej w pliku XML. Każdy schemat jest otwierany jako plik tymczasowy. Schematy mogą być zapisywane na dysku, dodawane do projektu lub odrzucane.

## <a name="see-also"></a>Zobacz też

- [Edytor XML](../xml-tools/xml-editor.md)
