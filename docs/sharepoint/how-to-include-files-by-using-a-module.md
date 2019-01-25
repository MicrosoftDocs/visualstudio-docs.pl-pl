---
title: 'Instrukcje: Dołączanie plików za pomocą modułu | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, modules
- modules [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0c08e04dd6ca95e691c33ce77bdedf6a655ee5b4
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871731"
---
# <a name="how-to-include-files-by-using-a-module"></a>Instrukcje: Dołączanie plików za pomocą modułu
  *Moduły* (nie należy mylić z [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] modułów) to kontenery, które umożliwia wdrażanie obrazów, plików tekstowych lub plików, takich jak strony wzorcowe ASPX w programie SharePoint.  
  
 Możesz wdrożyć plik do biblioteki dokumentów lub jako zwykłego pliku (np. default.aspx) poza bibliotekę dokumentów. Aby dodać plik do biblioteki dokumentów, należy określić `Type="GhostableInLibrary"` jako atrybut w **pliku** elementu. To ustawienie powoduje, że Utwórz element listy, aby przejść z plikiem, gdy zostanie dodany do biblioteki programu SharePoint. Aby wdrożyć plik poza bibliotekę dokumentów, albo określić `Type="Ghostable"` lub po prostu pominąć **typu** atrybutu.  
  
## <a name="add-a-module-to-a-sharepoint-solution"></a>Dodaj moduł do rozwiązania programu SharePoint  
  
#### <a name="to-add-a-module"></a>Aby dodać moduł  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Otwórz lub Utwórz projekt programu SharePoint.  
  
     Aby uzyskać więcej informacji, zobacz [SharePoint szablony elementu projektu i projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  W **Eksploratora rozwiązań**, wybierz węzeł projektu, a następnie na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
     **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
3.  Na liście szablonów programu SharePoint, wybierz opcję **modułu** szablonu, a następnie wybierz **Dodaj** przycisku.  
  
     W tym kroku tworzy węzeł w projekcie o nazwie Module1.  
  
4.  W obszarze Module1, Usuń *przykład.txt* pliku.  
  
     Przykład.txt znajduje się we wszystkich modułach nowy przykład celów i nie jest potrzebna. (Należy pamiętać, że usunięcie pliku spowoduje również usunięcie jego wpis z modułu *Elements.xml* pliku.)  
  
5.  Pliki do wdrożenia na strukturę określonego folderu w programie SharePoint, utworzyć te foldery, w obszarze Module1 w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , wybierając węzeł Module1, a następnie na pasku menu, wybierając **projektu**, **New Folder**.  
  
6.  Wybierz folder, w której chcesz dodać plik, a następnie na pasku menu wybierz **projektu**, **Dodaj istniejący element**.  
  
7.  Wybierz jeden lub więcej plików, które mają być wdrażane do programu SharePoint, a następnie wybierz **Dodaj** przycisku.  
  
     Po dodaniu pliku do projektu wpis dla niej jest automatycznie dodawane do pliku Elements.xml modułu. Podczas wdrażania projektu pliki są kopiowane do programu SharePoint server względem katalogu głównego projektu, która jest określona przez **pliku** elementu **adresu Url** atrybutów, takich jak `Url="Module1/New Folder/SomeFile.doc`. Jeśli chcesz zmienić lokalizację wdrażania dla pliku, albo przenieść do innego folderu w **Eksploratora rozwiązań** lub zmienić jego **adresu Url** ustawienie.  
  
8.  Wszystkie pliki, które mają być wyświetlane w bibliotece dokumentów, można dołączyć `Type="GhostableInLibrary"` atrybutu do swojego wpisu w *Elements.xml*. Na przykład  
  
    ```xml  
    <File Path="Module1\Some Folder\SomePage.aspx" Url="Module1/Some Folder/SomePage.aspx" Type="GhostableInLibrary" />  
    ```  
  
9. Wdrażanie projektu.  
  
     Skopiuj pliki do określonej lokalizacji w programie SharePoint.  
  
## <a name="see-also"></a>Zobacz także
 [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
