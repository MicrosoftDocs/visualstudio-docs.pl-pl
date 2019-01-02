---
title: 'Instrukcje: Mapowanie schematów z dokumentami programu Word w programie Visual Studio'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML schemas [Office development in Visual Studio], mapping
- mappings [Office development in Visual Studio], XML schemas to Word documents
- Word [Office development in Visual Studio], mapping XML schemas
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: fcd9d63b691096f0ace035e1e8384f904578f411
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867829"
---
# <a name="how-to-map-schemas-to-word-documents-inside-visual-studio"></a>Instrukcje: Mapowanie schematów z dokumentami programu Word w programie Visual Studio
  **Ważne** informacji zawartych w tym temacie dotyczące programu Microsoft Word jest prezentowane wyłącznie do korzyści i korzystanie z innym osobom oraz organizacjom, którzy znajdują się poza w Stanach Zjednoczonych i ich terytoriach lub korzystających z lub tworzenie programy, korzystających z produktów Microsoft Word, które są licencjonowane przez firmę Microsoft przed 2010 stycznia, po usunięciu implementację funkcji określonej przez Microsoft związane z niestandardowy kod XML z programu Microsoft Word. Te informacje dotyczące programu Microsoft Word nie mogą być odczytywane lub używane przez osoby i organizacje w Stanach Zjednoczonych lub jego terytoria, którzy za pomocą lub opracowywanie programów uruchamianych na produkty Microsoft Word, które są licencjonowane przez firmę Microsoft, po 10 stycznia 2010 r. ; te produkty będą nie działa tak samo jako produkty licencjonowane przed tą datą lub kupić i licencjonowane do użycia poza Stanami Zjednoczonymi.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Gdy dokument jest otwarty w programie Visual Studio, można mapować do dokumentu schematu XML. Możesz użyć tych samych narzędzi Microsoft Office Word, których używasz, gdy dokument jest otwarty poza programem Visual Studio. Office project tworzy te same obiekty, czy mapowanie schematu dokumentu przed lub po utworzeniu rozwiązania programu Word.  
  
## <a name="to-map-an-xml-schema-to-a-word-document-in-visual-studio"></a>Aby zamapować schematu XML do dokumentu programu Word w programie Visual Studio  
  
1.  Otwórz projekt dokumentem lub szablonem programu Word w programie Visual Studio.  
  
2.  Kliknij w dokumencie, aby przenieść fokus do projektanta.  
  
3.  Na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, najpierw musisz wyświetlić. Aby uzyskać więcej informacji, zobacz [jak: Pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  W **XML** grupy, kliknij przycisk **schematu**.  
  
     **Szablony i dodatki** zostanie otwarte okno dialogowe.  
  
5.  Kliknij przycisk **schematu XML** kartę.  
  
6.  Kliknij przycisk **schemat Dodaj**.  
  
     **Schemat Dodaj** zostanie otwarte okno dialogowe.  
  
7.  Przejdź do pliku schematu, zaznacz go, a następnie kliknij **Otwórz**.  
  
     **Schemat ustawień** zostanie otwarte okno dialogowe.  
  
8.  Przypisać aliasu lub kliknij przycisk **OK** można dodać schematu bez aliasu.  
  
9. Kliknij przycisk **OK**.  
  
     **Struktury XML** zostanie otwarte okno.  
  
10. Przeciągnij elementy z **struktury XML** okna do miejsc w dokumencie, w którym ma odpowiednie metody kontroli ma zostać utworzony.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Mapowanie schematów z arkuszami w programie Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Schematy XML i dane dostosowywane na poziomie dokumentu](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
