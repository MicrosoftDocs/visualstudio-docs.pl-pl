---
title: Łączenie wariantów użycia z dokumentami i diagramami | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties.artifactlink
- vs.teamarch.usecasediagram.artifact
helpviewer_keywords:
- use case diagrams
ms.assetid: 4c9ed205-9197-4ed5-b39d-ddfa24a0a421
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a5b4ef580825115a1d44c3abb39404332a4277ea
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787916"
---
# <a name="link-a-use-case-to-documents-and-diagrams"></a>Łączenie przypadków użycia z dokumentami i diagramami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz połączyć przypadek użycia na diagramie przypadku użycia innego diagramu lub dokumentu. Na przykład można połączyć przypadek użycia, następujące diagramy i dokumenty:  
  
- Diagram sekwencji, który pokazuje, jak cele przypadek użycia są realizowane przez interakcje między użytkownikami i system lub jej główne składniki.  
  
- Diagram aktywności, który pokazuje szczegółowe akcje użytkowników i systemu lub jego głównych składnikach, czyli podczas faktycznego wykonywania przypadku użycia.  
  
- Strony programu OneNote lub akapit, który opisuje przypadek użycia szczegółowo.  
  
- Dokument programu Word lub prezentacji programu PowerPoint, opisujący przypadek użycia szczegółowo. Możesz zachować tych dokumentów w rozwiązaniu lub w lokalizacji dostępne dla swojego zespołu, takich jak witryny programu SharePoint.  
  
  Aby połączyć przypadek użycia dokumentu, tworzenie artefaktów na diagram przypadków użycia i połączyć przypadek użycia z artefaktem. Właściwości artefaktów służy do Ustaw ścieżkę do pliku diagramu lub dokumentu. Zostanie otwarty po dwukrotnym kliknięciu artefaktu, diagram lub dokumentu.  
  
  Można podłączyć jako wiele artefaktów do każdego przypadek użycia, jak chcesz. Możliwe jest także łączenie artefaktów do innych rodzajów elementów na diagramie przypadków użycia.  
  
### <a name="to-open-a-document-associated-with-an-artifact"></a>Aby otworzyć dokument skojarzony z artefaktem  
  
-   Na diagramie przypadków użycia kliknij dwukrotnie kształt artefaktu.  
  
     Powiązany dokument zostanie otwarty.  
  
### <a name="to-link-a-use-case-to-a-diagram-or-file-in-the-same-solution"></a>Aby połączyć przypadek użycia na diagramie lub pliku w tym samym rozwiązaniu  
  
1.  Rysowanie diagramu, takich jak diagram sekwencji lub diagram aktywności, aby zilustrować scenariusza przypadku użycia.  
  
2.  Wróć do diagram przypadków użycia.  
  
3.  Przeciągnij na diagramie lub w pliku z Eksploratora rozwiązań na pustą część diagramu przypadków użycia.  
  
4.  Łączenie z artefaktu do przypadków użycia za pomocą **zależności**.  
  
### <a name="to-link-to-a-solution-file-such-as-a-word-document-or-powerpoint-presentation"></a>Aby utworzyć łącze do pliku rozwiązania, takie jak dokument programu Word lub prezentacji programu PowerPoint  
  
1.  Dodaj dokument do rozwiązania.  
  
    1.  W tym samym folderze Windows jako rozwiązanie, należy przenieść dokument programu Word.  
  
    2.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wskaż opcję **Dodaj**, a następnie kliknij przycisk **istniejący element**.  
  
    3.  Przejdź do dokumentu programu Word, a następnie kliknij przycisk **Dodaj**.  
  
         Dokument programu Word pojawia się w folderze rozwiązania w Eksploratorze rozwiązań.  
  
2.  Przeciągnij dokument programu Word za pomocą Eksploratora rozwiązań na pustą część diagramu przypadków użycia.  
  
     Pojawi się nowy artefaktu.  
  
3.  Łączenie z artefaktu do przypadków użycia za pomocą **zależności**.  
  
### <a name="to-link-to-a-shared-document-onenote-element-or-web-page"></a>Aby utworzyć łącze do dokumentu udostępnionego, OneNote element lub strony sieci web  
  
1.  Uzyskaj adres URL udostępniony element. Może to być na przykład początku ścieżki pliku sieci "\\\\", lub strony sieci web lub początkowy adres URL programu Sharepoint "http://" lub łącze do sekcji programu OneNote, strony, akapitu początku "onenote:".  
  
2.  W przyborniku kliknij **artefaktu** a następnie kliknij przycisk na diagramie przypadku użycia.  
  
3.  Za pomocą nowego artefaktu wybrane, wpisz lub wklej adres URL do **hiperłącze** właściwości.  
  
    > [!NOTE]
    >  Jeśli chcesz podać ścieżkę do pliku, najlepiej w typowych obszaru roboczego wybierz plik (począwszy od "\\\\"), lub pliku w ramach rozwiązania Visual Studio. Dzięki temu ścieżkę pliku pozostanie prawidłowe dla komputera innego członka zespołu, czy rozwiązanie jest przenoszony. Aby dodać dokument, takie jak dokument programu Word do rozwiązania, kliknij prawym przyciskiem myszy rozwiązanie w Eksploratorze rozwiązań, wskaż opcję **Dodaj** a następnie kliknij przycisk **istniejący element**.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagramy przypadków użycia UML: odwołanie](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagramy przypadków użycia UML: wskazówki](../modeling/uml-use-case-diagrams-guidelines.md)   
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)



