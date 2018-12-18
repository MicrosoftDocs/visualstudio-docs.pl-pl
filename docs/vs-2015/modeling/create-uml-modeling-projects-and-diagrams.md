---
title: Tworzenie projektów modelowania UML i diagramów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.addnewdiagramdialog
- vs.teamarch.createnewmodelingprojectdialog
helpviewer_keywords:
- projects [Visual Studio ALM], modeling
- diagrams - modeling, modeling
- modeling diagrams
- projects, UML
- UML, deleting diagrams
- UML
- UML diagrams, adding
- UML, projects
- Visual Studio ALM, modeling projects
- modeling projects
- UML diagrams
- projects, modeling
ms.assetid: c178b04b-4fd2-4bed-97e3-d793dae8649c
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5d841c9fde677eb4a8fb17e952a817364dab277e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738393"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Tworzenie projektów i diagramów modelowania UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

UML modeli pomagają zrozumieć, omówienia i projektowanie systemów oprogramowania. Program Visual Studio udostępnia szablony dla 5 najczęściej używanych diagramów UML: działania, klasy, składnika, sekwencja i przypadek użycia. Ponadto można tworzyć diagramy warstwowe, które ułatwiają definiują strukturę Twojego systemu.  
  
 Diagramy modelowania UML i diagramy warstwowe, może istnieć tylko wewnątrz projektu modelowania. Każdy projekt modelowania zawiera udostępnionego modelu UML i diagramów UML kilka. Każdy diagram jest widoku częściowego w modelu. UML model zawiera wszystkie elementy na diagramach UML i mogą być wyświetlane przy użyciu Eksploratora modelu UML. Aby uzyskać informacji na temat modeli i ich związek z diagramów, zobacz [modeli i diagramów UML Edytuj](../modeling/edit-uml-models-and-diagrams.md). Aby dowiedzieć się, jak modelowanie projektów pod kontrolą wersji, zobacz [Zarządzanie modelami i diagramami w ramach kontroli wersji](../modeling/manage-models-and-diagrams-under-version-control.md) i [struktury rozwiązania modelowania](../modeling/structure-your-modeling-solution.md)  
  
> [!NOTE]
>  Istnieje inny rodzaj diagramów, diagram klas platformy .NET, który jest używany w celu wizualizacji kodu programu. Aby uzyskać więcej informacji, zobacz [projektowanie i wyświetlanie klas i typów](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
##  <a name="CreatingModelingDiagrams"></a> Tworzenie diagramu w projekcie modelowania  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Aby utworzyć diagram i dodaj go do projektu  
  
1. Na **architektury** menu, wybierz **nowe UML lub diagramu warstwowego**.  
  
2. W **Dodaj nowy Diagram** okna dialogowego kliknij typ diagramu modelowania, który chcesz.  
  
    ![Dodaj okno dialogowe Nowy Diagram](../modeling/media/uml-adddiagram.png "UML_AddDiagram")  
  
3. Wpisz nazwę dla nowego diagramu.  
  
4. W **Dodaj do projektu modelowania** pola:  
  
   - Wybierz projekt modelowania, który już istnieje w rozwiązaniu, a następnie kliknij przycisk **OK**.  
  
     \- lub —  
  
   1.  Wybierz **Utwórz nowy projekt modelowania**, a następnie kliknij przycisk **OK**.  
  
   2.  W **Utwórz nowy projekt modelowania** okno dialogowe, wpisz nazwę i lokalizację nowego projektu, a następnie kliknij przycisk **OK**.  
  
        ![Tworzenie okna dialogowego Nowy projekt modelowania](../modeling/media/uml-createmodel.png "UML_CreateModel")  
  
        Jeśli Twoje rozwiązanie jest otwarte, nowy projekt zostanie dodany do rozwiązania. Jeśli nie masz żadnych Otwórz rozwiązanie, możesz wpisać nazwę dla nowego rozwiązania.  
  
   Jeśli masz już projekt modelowania, można również użyć poniższej procedury.  
  
#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Aby dodać diagram do istniejącego projektu modelowania  
  
1.  W **Eksploratora rozwiązań**, kliknij przycisk modelowania węzeł projektu.  
  
    > [!NOTE]
    >  Projekt modelowania zawiera definicję modelu folder o nazwie **ModelDefinition**.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element -**  *\<Nazwa projektu >* okno dialogowe, w obszarze **szablony**, kliknij przycisk modelowania diagram typu, na przykład **UML Diagram składników**.  
  
4.  Wpisz nazwę diagramu, a następnie kliknij przycisk **Dodaj**.  
  
     Na diagramie modelowania otwiera i pojawia się w projekcie modelowania.  
  
    > [!CAUTION]
    >  Nie Dodawanie, kopiowanie lub przeciągnij istniejące pliki diagramu, do innych projektów modelowania lub w innych lokalizacjach w rozwiązaniu. To powoduje, że elementy są usuwane z diagramów skopiowany lub błędy po otwarciu diagramów. Należy otworzyć plik diagramu z projektu modelowania, w której został utworzony. Jest to spowodowane diagramu UML jest widokiem modelu, który jest własnością jego projektu modelowania. Aby skopiować plik diagramu, Utwórz nowy diagram, a następnie skopiuj elementy z diagramu źródłowego do nowego diagramu. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z projekty modelowania i diagramy](#TroubleshootingModelingProjects).  
  
#### <a name="to-create-a-blank-modeling-project"></a>Aby utworzyć pusty projekt modelowania  
  
1.  Na **pliku** menu wskaż **New**, a następnie kliknij przycisk **projektu**.  
  
2.  W **nowy projekt** dialogowego **zainstalowane szablony**, kliknij przycisk **projekty modelowania**.  
  
3.  W środkowym oknie kliknij **projektu modelowania**.  
  
4.  Nazwij projekt, a następnie określ lokalizację, w **nazwa** i **lokalizacji** pola.  
  
5.  W **rozwiązania** wybierz opcję **Dodaj do rozwiązania** Aby dodać nowy projekt do rozwiązania już otwarte; lub **Utwórz nowe rozwiązanie** Zamknij wszystkie otwarte rozwiązanie, a następnie dodać Projekt do nowego rozwiązania.  
  
##  <a name="RemovingModelingDiagrams"></a> Usuwanie diagramów z projektu modelowania  
 Aby trwale usunąć diagramu lub można tymczasowo wyłączyć diagramu z projektem, a następnie przywróć ją.  
  
#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Aby trwale skasować diagramu z projektu  
  
-   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy główny plik, który reprezentuje diagramu, a następnie kliknij przycisk **Usuń**.  
  
     Diagram zostanie usunięty z projektu i jego systemu plików. Elementy wyświetlane na diagramie nie są usuwane z **Eksploratora modelu UML**.  
  
    > [!NOTE]
    >  Każdy diagram ma dwa pliki, co zależnej od firmy Microsoft do drugiego. Na przykład, jeśli masz diagram składników o nazwie `CD1`, należy usunąć plik o nazwie `CD1.componentdiagram`. Jego pomocniczy plik o nazwie `CD1.componentdiagram.layout` zostaną automatycznie usunięte.  
  
#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Aby tymczasowo wyłączyć diagramu z projektu  
  
-   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik diagramu, a następnie kliknij przycisk **Wyklucz z projektu**.  
  
     Diagram jest usuwany z projektu. Nie zostanie usunięty z systemu plików.  
  
    > [!NOTE]
    >  Elementy wyświetlane na diagramie nie są usuwane z **Eksploratora modelu UML**.  
  
#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Aby przywrócić wykluczonych czasowo diagramu do projektu  
  
1.  W **Eksploratora rozwiązań**, kliknij przycisk modelowania węzeł projektu.  
  
    > [!NOTE]
    >  Projekt modelowania zawiera definicję modelu folder o nazwie **ModelDefinition**.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.  
  
3.  W **Dodaj istniejący element** okno dialogowe, zlokalizuj plik diagramu, wybierz plik a następnie kliknij przycisk **Dodaj**.  
  
     Na diagramie modelowania otwiera i pojawia się w projekcie modelowania.  
  
    > [!NOTE]
    >  Każdy diagram ma parę plików w systemie plików. Nie należy wybierać pliku, który ma rozszerzenie `.layout`. Ponadto program Visual Studio nie obsługuje dodawania istniejących diagramów UML do wielu projektów modelowania. Każdy plik diagramu musi być otwarty w projekcie modelowania, w której został utworzony. Jest to spowodowane diagramu UML przedstawiono widok modelu, który jest własnością jego projektu modelowania.  
  
##  <a name="NonModelDiagrams"></a> Diagramy, które nie wymagają projekty modelowania  
 Następujące rodzaje diagramów nie są częścią projektu modelowania:  
  
-   Diagramy klas, które są tworzone jako widoki kodu źródłowego. Nie są one związane z diagramów klas UML. Aby uzyskać więcej informacji, zobacz [projektowanie i wyświetlanie klas i typów](../ide/designing-and-viewing-classes-and-types.md).  
  
-   Mapy kodu. Zobacz [mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).  
  
-   Diagramy, które nie są diagramów UML i diagramy warstwowe, takich jak języki specyficzne dla domeny.  
  
##  <a name="TroubleshootingModelingProjects"></a> Rozwiązywanie problemów z projektów i diagramów modelowania  
 W poniższej tabeli opisano problemy, które występują w ich rozwiązania lub diagramów i projektów modelowych:  
  
|**Problem**|**Powoduje, że**|**Rozdzielczość**|  
|---------------|----------------|--------------------|  
|Projekt modelowania nie można otworzyć ani ładowane do rozwiązania.<br /><br /> Zostanie wyświetlony następujący komunikat:<br /><br /> "Jeden lub więcej projektów w rozwiązaniu nie zostały poprawnie załadowane. Zobacz okno danych wyjściowych, aby uzyskać szczegółowe informacje."<br /><br /> W oknie danych wyjściowych wyświetla następujący komunikat:<br /><br /> "*ModelingProjectFilenameAndPath*.modelproj: błąd: format nierozpoznanym identyfikatorem Guid."|Projekt modelowania zawiera odwołania do projektów, które mają taką samą nazwę i znajdują się w tym samym rozwiązaniu.<br /><br /> Na przykład warstwa jest połączona z projektami, które mają taką samą nazwę i znajdują się w tym samym rozwiązaniu.|Użyj edytora tekstów, aby otworzyć projekt modelowania plików, usunięcie odwołań, a następnie spróbuj ponownie otworzyć projekt modelowania.<br /><br /> Aby uniknąć tego problemu, nie należy dodawać odwołań do projektów, które mają taką samą nazwę. Upewnij się, że projekt ma unikatowe nazwy.|  
|Elementy są nieobecne diagramy, które są dodawane, skopiowane lub przeciągnięte do innych projektów modelowania lub w innych lokalizacjach w rozwiązaniu.<br /><br /> - lub -<br /><br /> Przy próbie otwarcia diagramu, są wyświetlane następujące komunikaty:<br /><br /> — "Niektóre kształtów i łączników na diagramie Brak, ponieważ nie istnieją w tym projekcie ich definicje. Albo definicje zostały usunięte z modelu podczas diagram został zamknięty lub diagramu zostały skopiowane do innego projektu, który nie zawiera tych definicji."<br /><br /> - lub -<br /><br /> -"Ten dokument jest otwarty przez inny projekt."|Plik diagramu został dodany, przeciągnąć lub skopiowane z projektu modelowania do innego projektu modelowania lub w innej lokalizacji w rozwiązaniu.|Aby skopiować plik diagramu, Utwórz nowy diagram, a następnie skopiuj elementy z diagramu źródłowego do nowego diagramu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Tworzenie struktury rozwiązania modelowania](../modeling/structure-your-modeling-solution.md)



