---
title: Tworzenie projektów i diagramów modelowania UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 52c55b2cfdf000d91a83071b53e8e9450187b720
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852021"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Tworzenie projektów i diagramów modelowania UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modele UML pomagają zrozumieć, omówić i projektować systemy oprogramowania. Program Visual Studio udostępnia szablony dla pięciu najczęściej używanych diagramów UML: działania, klasy, składnika, sekwencji i przypadku użycia. Ponadto można tworzyć diagramy warstwowe, które ułatwiają Definiowanie struktury systemu.

 Diagramy modelowania UML i Diagramy warstw mogą istnieć tylko wewnątrz projektu modelowania. Każdy projekt modelowania zawiera współużytkowany model UML i kilka diagramów UML. Każdy diagram jest częściowym widokiem modelu. Model UML zawiera wszystkie elementy na diagramach UML i można go wyświetlić za pomocą Eksploratora modelu UML. Aby uzyskać informacje o modelach i ich relacji z diagramami, zobacz [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md). Aby uzyskać informacje na temat modelowania projektów w ramach kontroli wersji, zobacz [Zarządzanie modelami i diagramami w ramach kontroli wersji](../modeling/manage-models-and-diagrams-under-version-control.md) i tworzenie [struktury rozwiązania modelowania](../modeling/structure-your-modeling-solution.md)

> [!NOTE]
> Istnieje inny rodzaj diagramu — Diagram klas .NET, który służy do wizualizacji kodu programu. Aby uzyskać więcej informacji, zobacz [projektowanie i wyświetlanie klas i typów](https://msdn.microsoft.com/library/ab7aty24.aspx).

## <a name="create-a-diagram-in-a-modeling-project"></a><a name="CreatingModelingDiagrams"></a> Tworzenie diagramu w projekcie modelowania
 Aby sprawdzić, które wersje programu Visual Studio obsługują tę funkcję, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Aby utworzyć diagram i dodać go do projektu

1. W menu **Architektura** wybierz kolejno pozycje **Nowy UML lub diagram warstwowy**.

2. W oknie dialogowym **Dodaj nowy diagram** kliknij żądany typ diagramu modelowania.

    ![Okno dialogowe Dodawanie nowego diagramu](../modeling/media/uml-adddiagram.png "UML_AddDiagram")

3. Wpisz nazwę nowego diagramu.

4. W polu **Dodaj do projektu modelowania** :

   - Wybierz projekt modelowania, który już istnieje w rozwiązaniu, a następnie kliknij przycisk **OK**.

     \- oraz

   1. Wybierz pozycję **Utwórz nowy projekt modelowania**, a następnie kliknij przycisk **OK**.

   2. W oknie dialogowym **Utwórz nowy projekt modelowania** wpisz nazwę i lokalizację nowego projektu, a następnie kliknij przycisk **OK**.

        ![Okno dialogowe Tworzenie nowego projektu modelowania](../modeling/media/uml-createmodel.png "UML_CreateModel")

        Jeśli Twoje rozwiązanie jest otwarte, nowy projekt zostanie dodany do rozwiązania. Jeśli nie masz otwartego rozwiązania, możesz wpisać nazwę nowego rozwiązania.

   Jeśli masz już projekt modelowania, możesz również użyć poniższej procedury.

#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Aby dodać diagram do istniejącego projektu modelowania

1. W **Eksplorator rozwiązań**kliknij węzeł projekt modelowania.

    > [!NOTE]
    > Projekt modelowania zawiera folder definicji modelu o nazwie **ModelDefinition**.

2. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

3. W oknie dialogowym **Dodaj nowy element —** w *\<project name>* obszarze **Szablony**kliknij typ diagramu modelowania, na przykład **diagram składników UML**.

4. Wpisz nazwę diagramu, a następnie kliknij przycisk **Dodaj**.

     Diagram modelowania zostanie otwarty i pojawi się w projekcie modelowania.

    > [!CAUTION]
    > Nie dodawaj, Kopiuj ani nie przeciągaj istniejących plików diagramu do innych projektów modelowania lub do innych lokalizacji w rozwiązaniu. Powoduje to, że elementy, które mają zniknąć z skopiowanych diagramów lub błędów, pojawiają się po otwarciu diagramów. Należy otworzyć plik diagramu z projektu modelowania, w którym został utworzony. Jest to spowodowane tym, że diagram UML jest widokiem modelu, który jest własnością projektu modelowania. Aby skopiować plik diagramu, Utwórz nowy diagram, a następnie skopiuj elementy z diagramu źródłowego do nowego diagramu. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z modelami i diagramami modelowania](#TroubleshootingModelingProjects).

#### <a name="to-create-a-blank-modeling-project"></a>Aby utworzyć pusty projekt modelowania

1. W menu **plik** wskaż polecenie **Nowy**, a następnie kliknij pozycję **projekt**.

2. W oknie dialogowym **Nowy projekt** w obszarze **zainstalowane szablony**kliknij pozycję **projekty modelowania**.

3. W środkowym oknie kliknij pozycję **projekt modelowania**.

4. Nazwij projekt i określ lokalizację w polach **Nazwa** i **Lokalizacja** .

5. W polu **rozwiązanie** wybierz pozycję **Dodaj do rozwiązania** , aby dodać nowy projekt do już otwartego rozwiązania. lub **Utwórz nowe rozwiązanie** , aby zamknąć otwarte rozwiązanie i dodać projekt do nowego rozwiązania.

## <a name="removing-modeling-diagrams-from-a-project"></a><a name="RemovingModelingDiagrams"></a> Usuwanie diagramów modelowania z projektu
 Można trwale usunąć diagram lub można tymczasowo wykluczyć diagram z projektu, a następnie go przywrócić.

#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Aby trwale usunąć diagram z projektu

- W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy główny plik reprezentujący diagram, a następnie kliknij polecenie **Usuń**.

     Diagram zostanie usunięty z projektu i systemu plików. Elementy wyświetlane na diagramie nie są usuwane z **Eksploratora modelu UML**.

    > [!NOTE]
    > Każdy diagram ma dwa pliki — jeden oddziału. Na przykład jeśli masz diagram składników o nazwie `CD1` , należy usunąć plik o nazwie `CD1.componentdiagram` . Jego plik pomocniczy o nazwie `CD1.componentdiagram.layout` zostanie usunięty automatycznie.

#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Aby tymczasowo wykluczyć diagram z projektu

- W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik diagramu, a następnie kliknij pozycję **Wyklucz z projektu**.

     Diagram zostanie usunięty z projektu. Nie jest on usuwany z systemu plików.

    > [!NOTE]
    > Elementy wyświetlane na diagramie nie są usuwane z **Eksploratora modelu UML**.

#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Aby przywrócić tymczasowo wykluczony diagram do projektu

1. W **Eksplorator rozwiązań**kliknij węzeł projekt modelowania.

    > [!NOTE]
    > Projekt modelowania zawiera folder definicji modelu o nazwie **ModelDefinition**.

2. W menu **projekt** kliknij polecenie **Dodaj istniejący element**.

3. W oknie dialogowym **Dodaj istniejący element** Znajdź plik diagramu, wybierz plik, a następnie kliknij przycisk **Dodaj**.

     Diagram modelowania zostanie otwarty i pojawi się w projekcie modelowania.

    > [!NOTE]
    > Każdy diagram ma parę plików w systemie plików. Nie wybieraj pliku, który ma rozszerzenie `.layout` . Ponadto program Visual Studio nie obsługuje dodawania istniejących diagramów UML do wielu projektów modelowania. Każdy plik diagramu musi być otwarty w projekcie modelowania, w którym został utworzony. Dzieje się tak, ponieważ diagram UML przedstawia widok modelu, który jest własnością projektu modelowania.

## <a name="diagrams-that-do-not-require-modeling-projects"></a><a name="NonModelDiagrams"></a> Diagramy, które nie wymagają projektów modelowania
 Następujące rodzaje diagramów nie są częścią projektu modelowania:

- Diagramy klas, które są tworzone jako widoki kodu źródłowego. Nie są one powiązane z diagramami klas UML. Aby uzyskać więcej informacji, zobacz [projektowanie i wyświetlanie klas i typów](../ide/designing-and-viewing-classes-and-types.md).

- Mapy kodu. Zobacz [zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md).

- Diagramy, które nie są diagramami UML ani diagramami warstw, takich jak języki specyficzne dla domeny.

## <a name="troubleshooting-modeling-projects-and-diagrams"></a><a name="TroubleshootingModelingProjects"></a> Rozwiązywanie problemów z projektami i diagramami modelowania
 W poniższej tabeli opisano problemy, które mogą wystąpić w przypadku modelowania projektów lub diagramów oraz sposoby ich rozwiązywania:

|**Problem**|**Przyczyny**|**Rozdzielczość**|
|---------------|----------------|--------------------|
|Projekt modelowania nie może zostać otwarty ani załadowany do rozwiązania.<br /><br /> Zostanie wyświetlony następujący komunikat:<br /><br /> "Co najmniej jeden projekt w rozwiązaniu nie został poprawnie załadowany. Aby uzyskać szczegółowe informacje, zobacz Okno Dane wyjściowe ".<br /><br /> W oknie dane wyjściowe zostanie wyświetlony następujący komunikat:<br /><br /> "*ModelingProjectFilenameAndPath*. modelproj: błąd: nierozpoznany format identyfikatora GUID".|Projekt modelowania zawiera odwołania do projektów, które mają taką samą nazwę i znajdują się w tym samym rozwiązaniu.<br /><br /> Na przykład warstwa jest połączona z projektami o tej samej nazwie i znajdują się w tym samym rozwiązaniu.|Za pomocą edytora tekstów Otwórz plik projektu modelowania, Usuń odwołania, a następnie spróbuj ponownie otworzyć projekt modelowania.<br /><br /> Aby uniknąć tego problemu, nie należy dodawać odwołań do projektów, które mają taką samą nazwę. Upewnij się, że projekty mają unikatowe nazwy.|
|Brak elementów w diagramach, które są dodawane, kopiowane lub przeciągnięte do innych projektów modelowania lub do innych lokalizacji w rozwiązaniu.<br /><br /> — lub —<br /><br /> Podczas próby otwarcia diagramu wyświetlane są następujące komunikaty:<br /><br /> -Brak niektórych kształtów lub łączników na diagramie, ponieważ ich definicje nie istnieją w tym projekcie. Definicje zostały usunięte z modelu, podczas gdy diagram został zamknięty lub diagram został skopiowany do innego projektu, który nie zawiera tych definicji. "<br /><br /> — lub —<br /><br /> -"Ten dokument jest otwarty przez inny projekt".|Plik diagramu został dodany, przeciągnięty lub skopiowany z projektu modelowania do innego projektu modelowania lub do innej lokalizacji w rozwiązaniu.|Aby skopiować plik diagramu, Utwórz nowy diagram, a następnie skopiuj elementy z diagramu źródłowego do nowego diagramu.|

## <a name="see-also"></a>Zobacz też
 [Edycja modeli UML i diagramów](../modeling/edit-uml-models-and-diagrams.md) [struktury rozwiązania do modelowania](../modeling/structure-your-modeling-solution.md)
