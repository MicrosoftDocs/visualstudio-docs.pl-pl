---
title: 'Instrukcje: Importowanie tematu lub strony wzorcowej | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7341d12571143d2725b3dd05e5d8e9f03c7d9125
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53952924"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Instrukcje: Importowanie tematu lub strony wzorcowej
  Można nadać strony w witrynie programu SharePoint spójny wygląd, tworząc i za pomocą stron wzorcowych i motywów. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie zapewnia szablony dla tych elementów, ale można je utworzyć w programie SharePoint Designer, a następnie zaimportować je do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [bloków konstrukcyjnych: Strony i interfejs użytkownika](http://go.microsoft.com/fwlink/?LinkID=182095) w witrynie internetowej firmy Microsoft.  
  
### <a name="to-import-a-master-page-or-theme"></a>Aby importowanie tematu lub strony wzorcowej  
  
1.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Utwórz lub Otwórz projekt programu SharePoint.  
  
     Aby uzyskać informacje o sposobie tworzenia projektu programu SharePoint, zobacz [SharePoint szablony elementu projektu i projektu](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
3.  W **Dodaj nowy element** okna dialogowego rozwiń **SharePoint** węzła, a następnie wybierz **2010** węzła.  
  
4.  Na liście szablonów programu SharePoint, wybierz opcję **modułu** szablonu, a następnie określ nazwę dla modułu.  
  
     Moduł zawiera pliki (na przykład strony wzorcowej lub plików) do wdrożenia w określonej lokalizacji w programie SharePoint.  
  
5.  W module, należy usunąć domyślny plik o nazwie *przykład.txt*.  
  
6.  Wybierz węzeł modułu.  
  
7.  Na pasku menu wybierz **projektu** > **Dodaj istniejący element**, a następnie wybierz plik główny tematu lub strony.  
  
     Pliki strony wzorcowej z rozszerzeniem .master i plików z rozszerzeniem .thmx.  
  
8.  Jeśli dodano stronę wzorcową, zmienić jego **Rozwiązywanie konfliktów wdrażania** ustawienie **automatyczne** we właściwościach modułu.  
  
    > [!NOTE]  
    >  Mogą wystąpić błędy, jeśli nazwa strony wzorcowej jest taka sama jak nazwa istniejącej strony głównej, która jest oznaczona jako domyślna strona wzorcowa lub niestandardowej strony wzorcowej. Aby uzyskać informacje o sposobie rozwiązania tego problemu, zobacz [instruktażu: Importowanie niestandardowej strony wzorcowej oraz strony witryny z obrazem](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).  
  
9. W module, otwórz *Elements.xml*.  
  
     Należy zaktualizować *Elements.xml* plik, aby odwoływać się do strony głównej lub motyw, który został dodany.  
  
10. Dla strony wzorcowej Zastąp istniejący kod znaczników modułu następującym kodem.  
  
    ```xml  
    <Module Name="[Module Name]" Url="_catalogs/masterpage">  
        <File Path="[Module Name]\[Master Page Name].master"   
          Url="[Master Page Name].master" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Dla motywu należy zastąpić istniejące znaczniki modułu następującym kodem.  
  
    ```xml  
    <Module Name="[Module Name]" Url="_catalogs/theme"   
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme     
          Name].thmx" Type="GhostableInLibrary" />  
    </Module>  
    ```  
  
     Pamiętaj zastąpić symbole zastępcze nazwą rzeczywistego modułu i strony wzorcowej lub motywu.  
  
     Ten atrybut `Type="GhostableInLibrary"` wskazuje, że element został dodany do bazy danych zawartości i `Url` atrybutu modułu określa, gdzie można przechowywać plik w bazie danych zawartości programu SharePoint.  
  
11. Aby zmienić zakres wdrożenia dla strony wzorcowej w **Eksploratora rozwiązań**, otwórz plik funkcji w Projektancie funkcji, a następnie wybierz nowy zakres wdrożenia z **zakres** listy.  
  
     Wartość **Web** oznacza, że strona główna ma zastosowanie tylko do witryny sieci Web, która jest obecnie określone w projekcie. Wartość **witryny** oznacza, że strona główna ma zastosowanie do bieżącej kolekcji witryny, w tym wszystkie lokacje podrzędne i internetowego poziomu głównego. Inne wartości nie mają zastosowania.  
  
    > [!NOTE]  
    >  Ponieważ motywy można stosować tylko na poziomie zbioru witryn, zaleca się czy nie ustawisz zakres motyw do żadnego elementu innego niż **witryny**. Mogą wystąpić błędy, jeśli motyw jest używana w lokacji podrzędnej.  
  
12. Na pasku menu wybierz **kompilacji** > **wdrożyć rozwiązanie**.  
  
13. Aby sprawdzić, czy pliki zostały poprawnie wdrożone, otwórz witrynę programu SharePoint, wybierz polecenie **Akcje witryny** menu, wybierz **ustawienia lokacji** polecenia, a następnie wybierz opcję **stronami wzorcowymi**  łącze lub **motywy** łącza.  
  
     Lista stron wzorcowych i motywów pojawia się i zawiera strony wzorcowej lub motywu, który można zaimportować.  
  
## <a name="see-also"></a>Zobacz także
 [Strony wzorcowe](http://go.microsoft.com/fwlink/?LinkId=184955)   
 [Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)   
 [Tworzenie stron dla SharePoint](../sharepoint/creating-pages-for-sharepoint.md)   
 [Użyj modułów, aby uwzględnić pliki w rozwiązaniu](../sharepoint/using-modules-to-include-files-in-the-solution.md)  
