---
title: 'Instrukcje: Importowanie strony wzorcowej lub motywu | Microsoft Docs'
description: Utwórz szablony dla stron głównych i motywów w programie SharePoint Designer, a następnie zaimportuj do programu Visual Studio, aby zapewnić spójny wygląd stron w witrynie programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c17f4e7477a20ea245eaa359a6f9611a8dc4ece6
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903497"
---
# <a name="how-to-import-a-master-page-or-theme"></a>Instrukcje: Importowanie strony wzorcowej lub motywu
  Możesz nadać stronom w witrynie programu SharePoint spójny wygląd, tworząc i używając stron wzorcowych i motywów. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nie udostępnia szablonów dla tych elementów, ale można je utworzyć w programie SharePoint Designer, a następnie zaimportować je do programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Aby uzyskać więcej informacji, zobacz [Budowanie bloków: strony i interfejs użytkownika](/previous-versions/office/developer/sharepoint-2010/ee539040(v=office.14)) w witrynie sieci Web firmy Microsoft.

### <a name="to-import-a-master-page-or-theme"></a>Aby zaimportować stronę wzorcową lub motyw

1. W programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Utwórz lub Otwórz projekt programu SharePoint.

     Aby uzyskać informacje na temat sposobu tworzenia projektu programu SharePoint, zobacz [Szablony projektów i elementów projektu programu SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

3. W oknie dialogowym **Dodaj nowy element** rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

4. Na liście szablonów programu SharePoint wybierz szablon **modułu** , a następnie określ nazwę modułu.

     Moduł zawiera pliki (na przykład strony wzorcowe lub pliki motywu) do wdrożenia w lokalizacji określonej w programie SharePoint.

5. W module Usuń plik domyślny o nazwie *Sample.txt*.

6. Wybierz węzeł modułu.

7. Na pasku menu wybierz **projekt**  >  **Dodaj istniejący element**, a następnie wybierz stronę wzorcową lub plik motywu.

     Pliki stron głównych mają rozszerzenie. Master, a pliki motywów mają rozszerzenie. THMX.

8. Jeśli dodano stronę wzorcową, należy zmienić ustawienie **rozwiązywania konfliktów wdrożenia** na **Automatyczne** we właściwościach modułu.

    > [!NOTE]
    > Błędy mogą wystąpić, jeśli nazwa strony głównej jest taka sama jak nazwa istniejącej strony wzorcowej, która jest oznaczona jako domyślna Strona główna lub niestandardowa strona wzorcowa. Aby uzyskać informacje na temat sposobu rozwiązania tego problemu, zobacz [Przewodnik: Importowanie niestandardowej strony wzorcowej i strony witryny z obrazem](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md).

9. W module Otwórz *Elements.xml*.

     Należy zaktualizować plik *Elements.xml* , aby odwoływała się do dodanej strony wzorcowej lub motywu.

10. Dla strony wzorcowej Zastąp istniejący znacznik modułu następującym znacznikiem.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/masterpage">
        <File Path="[Module Name]\[Master Page Name].master"
          Url="[Master Page Name].master" Type="GhostableInLibrary" />
    </Module>
    ```

     W przypadku motywu Zastąp istniejący znacznik modułu następującym znacznikiem.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/theme"
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme
          Name].thmx" Type="GhostableInLibrary" />
    </Module>
    ```

     Pamiętaj, aby zastąpić wartości symboli zastępczych rzeczywistymi nazwami modułu oraz stroną wzorcową lub motywem.

     Ten atrybut `Type="GhostableInLibrary"` wskazuje, że element jest dodawany do bazy danych zawartości, a `Url` atrybut modułu określa miejsce przechowywania pliku w bazie danych zawartości programu SharePoint.

11. Aby zmienić zakres wdrożenia dla strony wzorcowej, w **Eksplorator rozwiązań** Otwórz plik funkcji w Projektancie funkcji, a następnie wybierz nowy zakres wdrożenia z listy **zakres** .

     Wartość **sieci Web** oznacza, że strona wzorcowa ma zastosowanie tylko do witryny sieci Web, która jest aktualnie określona w projekcie. Wartość **lokacji** oznacza, że strona wzorcowa ma zastosowanie do bieżącego zbioru witryn, który obejmuje wszystkie lokacje podrzędne i główną witrynę sieci Web. Inne wartości nie mają zastosowania.

    > [!NOTE]
    > Ponieważ motywy stosują się tylko do poziomu zbioru witryn, zalecamy, aby nie ustawiać zakresu motywu do elementów innych niż **lokacja**. Błędy mogą wystąpić, jeśli motyw jest używany w podwitrynie.

12. Na pasku menu wybierz kolejno opcje **kompilacja**  >  **Wdróż rozwiązanie**.

13. Aby sprawdzić, czy pliki zostały wdrożone prawidłowo, Otwórz witrynę programu SharePoint, wybierz menu **Akcje witryny** , wybierz polecenie **Ustawienia witryny** , a następnie wybierz łącze **strony główne** lub link **motywy** .

     Zostanie wyświetlona lista stron wzorcowych lub motywów, które zawierają zarówno stronę wzorcową, jak i zaimportowaną kompozycję.

## <a name="see-also"></a>Zobacz także
- [Strony wzorcowe](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14))
- [Importowanie elementów z istniejącej witryny programu SharePoint](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [Tworzenie stron dla programu SharePoint](../sharepoint/creating-pages-for-sharepoint.md)
- [Używanie modułów do dołączania plików w rozwiązaniu](../sharepoint/using-modules-to-include-files-in-the-solution.md)
