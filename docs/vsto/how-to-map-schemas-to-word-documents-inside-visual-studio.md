---
title: 'Instrukcje: mapowanie schematów do dokumentów programu Word w programie Visual Studio'
description: Dowiedz się, jak można zmapować schemat XML do dokumentu programu Microsoft Office Word, gdy dokument jest otwarty w programie Visual Studio.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 082d5fe4fbcc7f66709770c16d3c9a1a2811e60d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900930"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Instrukcje: mapowanie schematów do dokumentów programu Word w programie Visual Studio
  **Ważne** Informacje przedstawione w tym temacie dotyczące programu Microsoft Word są prezentowane wyłącznie na korzyść i użytkowanie przez osoby i organizacje, które znajdują się poza Stany Zjednoczoneą i jej terytoriami, lub opracowywaniem programów, które są uruchamiane w programie Microsoft Word, które zostały licencjonowane przez firmę Microsoft przed 2010 stycznia, gdy firma Microsoft usunie implementację konkretnych funkcji związanych z niestandardowym kodem XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word mogą nie być odczytane lub używane przez osoby lub organizacje w Stany Zjednoczone lub na terytoriach, którzy korzystają z programu lub opracowywania programów, które są uruchamiane w programie, produkty Microsoft Word, które zostały licencjonowane przez firmę Microsoft po 10 stycznia 2010; te produkty nie będą działać tak samo jak produkty licencjonowane przed tą datą lub zakupione i licencjonowane do użycia poza Stany Zjednoczone.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Schemat XML można zmapować do dokumentu, gdy dokument jest otwarty w programie Visual Studio. Używasz tych samych Microsoft Office narzędzi programu Word, które są używane, gdy dokument jest otwarty poza programem Visual Studio. Projekt pakietu Office tworzy te same obiekty niezależnie od tego, czy schemat został zmapowany do dokumentu przed lub po utworzeniu rozwiązania programu Word.

## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Aby zmapować schemat XML do dokumentu programu Word w programie Visual Studio

1. Otwórz dokument programu Word lub projekt szablonu wewnątrz programu Visual Studio.

2. Kliknij dokument, aby przenieść fokus do projektanta.

3. Na wstążce kliknij kartę **deweloper** .

    > [!NOTE]
    > Jeśli karta **deweloper** nie jest widoczna, należy ją najpierw pokazać. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

4. W grupie **XML** kliknij pozycję **schemat**.

     Zostanie otwarte okno dialogowe **Szablony i dodatki** .

5. Kliknij kartę **schemat XML** .

6. Kliknij pozycję **Dodaj schemat**.

     Zostanie otwarte okno dialogowe **Dodaj schemat** .

7. Przejdź do pliku schematu, zaznacz go, a następnie kliknij przycisk **Otwórz**.

     Zostanie otwarte okno dialogowe **Ustawienia schematu** .

8. Przypisz alias lub kliknij przycisk **OK** , aby dodać schemat bez aliasu.

9. Kliknij przycisk **OK**.

     Zostanie otwarte okno **struktury XML** .

10. Przeciągnij elementy z okna **struktury XML** do miejsc w dokumencie, w których chcesz utworzyć odpowiednie kontrolki.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: mapowanie schematów do arkuszy w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)
- [Schematy XML i dane w dostosowaniach na poziomie dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)
