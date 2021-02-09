---
title: Pakowanie i wdrażanie rozwiązań SharePoint | Microsoft Docs
description: Pakowanie i wdrażanie rozwiązań programu SharePoint, które są wdrażane na serwerze programu SharePoint przy użyciu pliku pakietu rozwiązań (wsp).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ae74aa3cf759ba006acd36c168eecceac4b2ee4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916548"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>Pakowanie i wdrażanie rozwiązań SharePoint
  Zazwyczaj rozwiązanie SharePoint jest wdrażane na serwerze programu SharePoint przy użyciu pliku pakietu rozwiązania (wsp). Za pomocą programu Visual Studio można organizować elementy projektu programu SharePoint w funkcje i utworzyć pakiet do wdrażania funkcji programu SharePoint.

 Ten temat zawiera następujące informacje:

- [Tworzenie funkcji i pakietów](#create-features-and-packages)

- [Obsługa narzędzi funkcji i pakietów](#feature-and-packaging-tool-support)

- [Wdrażanie rozwiązań SharePoint](#deploy-sharepoint-solutions)

- [Wdrażanie plików w rozwiązaniach SharePoint](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>Tworzenie funkcji i pakietów
 Możesz użyć programu Visual Studio, aby pogrupować powiązane elementy programu SharePoint w *funkcję*. Na przykład funkcja definicji listy kontaktów może zawierać wystąpienie listy i definicję listy. Te dwa elementy można połączyć w jedną funkcję na potrzeby wdrożenia. Aby uzyskać więcej informacji na temat funkcji, zobacz [Building Block: Features](/previous-versions/office/developer/sharepoint-2010/ee537350(v=office.14)).

 Następnie można utworzyć pakiet rozwiązania programu SharePoint (*wsp*) do łączenia wielu funkcji, definicji lokacji, zestawów i innych plików w jeden pakiet, w którym są przechowywane pliki w formacie wymaganym przez program SharePoint w celu wdrożenia plików na serwerze. Aby uzyskać więcej informacji, zobacz [Building Block: Solutions](/previous-versions/office/developer/sharepoint-2010/ee537008(v=office.14)).

## <a name="feature-and-packaging-tool-support"></a>Obsługa narzędzi funkcji i pakietów
 Możesz użyć narzędzi programistycznych programu SharePoint w programie Visual Studio, aby szybko organizować pliki programu SharePoint w funkcje i pakiety rozwiązań w celu łatwiejszego wdrażania. Aby skonfigurować funkcję i pakiet rozwiązania, można użyć następujących narzędzi.

- Projektant funkcji i Projektant pakietów.

- Eksplorator pakietów, okno narzędzia.

- Eksplorator rozwiązań.

### <a name="feature-designer-and-package-designer"></a>Projektant funkcji i Projektant pakietów
 Można tworzyć funkcje, ustawiać zakresy i oznaczyć inne funkcje jako zależności przy użyciu projektanta funkcji. Projektant wyświetla również końcowy plik XML, który opisuje każdą funkcję. Aby uzyskać więcej informacji, zobacz [Tworzenie funkcji programu SharePoint](../sharepoint/creating-sharepoint-features.md).

 Zastosuj funkcję do określonej witryny sieci Web lub grupy witryn sieci Web, ustawiając jej *zakres* w Projektancie funkcji. Jeśli funkcja jest aktywowana dla pojedynczej witryny sieci Web, funkcja działa tylko w tej konkretnej witrynie sieci Web. Jeśli funkcja jest aktywowana dla zbioru witryn, elementy w funkcji mają zastosowanie do całej kolekcji witryn. Aby uzyskać więcej informacji, zobacz [Zakres elementu](/previous-versions/office/developer/sharepoint-2010/ms476615(v=office.14)).

 Jeśli funkcja korzysta z innych funkcji, można ustawić *zależność aktywacji funkcji* , aby oznaczyć funkcje zależne przed udostępnieniem funkcji. Zależność aktywacji funkcji sprawdza, czy zależne funkcje są już aktywowane w tym zakresie. Aby uzyskać więcej informacji, zobacz [zależności aktywacji i zakres](/previous-versions/office/developer/sharepoint-2010/aa543162(v=office.14)).

 W projektancie pakietów można grupować elementy programu SharePoint w jednym pakiecie rozwiązań i konfigurować, czy serwer sieci Web ma być resetowany podczas wdrażania. Aby ustawić typ serwera wdrażania, użyj okna **Właściwości** . Projektant generuje również plik XML, który opisuje zawartość pakietu. Aby uzyskać więcej informacji, zobacz [Tworzenie pakietów rozwiązania SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).

 Podczas wdrażania usługa Internet Information Services (IIS) jest zatrzymana w celu skopiowania plików rozwiązania do serwera programu SharePoint. Korzystając z projektanta pakietów w programie Visual Studio, można wybrać, czy serwer sieci Web ma być uruchamiany ponownie. Aby skonfigurować, czy rozwiązanie jest wdrożone na serwerze frontonu sieci Web lub serwerze aplikacji, użyj okna **Właściwości** . Aby uzyskać więcej informacji, zobacz [element rozwiązania (rozwiązanie)](/previous-versions/office/developer/sharepoint-2010/ms412929(v=office.14)).

### <a name="packaging-explorer"></a>Eksplorator pakietów
 Aby uzupełnić projektanta funkcji i projektanta pakietów, można użyć Eksploratora pakietów do grupowania plików programu SharePoint w funkcje i pakiety. Ponadto można zobaczyć hierarchiczny widok pakietu, funkcji, elementów projektu programu SharePoint i plików. Eksplorator pakietów jest oknem narzędzia, za pomocą którego można wykonać następujące zadania:

- Otwórz elementy projektu programu SharePoint i pliki.

- Przeciągnij i upuść elementy projektu programu SharePoint z jednej funkcji do innej.

- Przeciągnij i upuść elementy projektu programu SharePoint i funkcje z jednego pakietu do innego.

- Dodaj nową funkcję do pakietu.

- Otwórz funkcję lub projektanta pakietów.

- Sprawdź poprawność funkcji i pakietów.

  Narzędzia deweloperskie programu SharePoint w programie Visual Studio mają reguły sprawdzania poprawności, aby pomóc w zapewnieniu prawidłowego tworzenia pakietu rozwiązania. Ponadto reguły sprawdzają, czy plik rozwiązania *wsp* można pomyślnie wdrożyć i aktywować na serwerze programu SharePoint. Aby uzyskać więcej informacji na temat schematu XML dla funkcji, zobacz [schematy funkcji](/previous-versions/office/developer/sharepoint-2010/ms414322(v=office.14)).

  Do systemu projektu programu SharePoint można dodawać niestandardowe reguły sprawdzania poprawności funkcji i pakietów. Aby uzyskać więcej informacji, zobacz [How to: Create Custom Feature and Package Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

  Aby uzyskać więcej informacji na temat Eksploratora pakietów, zobacz [How to: Dodawanie i usuwanie funkcji oraz elementów do pakietu przy użyciu Eksploratora pakietów](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

### <a name="solution-explorer"></a>Eksplorator rozwiązań
 Za pomocą Eksplorator rozwiązań można nawigować i otwierać pliki projektu programu SharePoint. Użyj menu kontekstowego w Eksplorator rozwiązań, aby dodać funkcje, odbiorniki zdarzeń funkcji i zasoby funkcji. Ponadto można otworzyć projektantów funkcji i projektantów pakietów, aby skonfigurować funkcje i pakiety do wdrożenia.

## <a name="deploy-sharepoint-solutions"></a>Wdrażanie rozwiązań SharePoint
 Po dostosowaniu funkcji i pakietów w programie Visual Studio można utworzyć plik *. wsp* do wdrożenia na serwerach programu SharePoint. Możesz użyć programu Visual Studio do debugowania i testowania. Program *wsp* tylko na serwerze programu SharePoint na komputerze deweloperskim. Aby uzyskać więcej informacji na temat sposobu wdrażania rozwiązań programu SharePoint na zdalnym serwerze programu SharePoint, zobacz [wdrażanie rozwiązania](/previous-versions/office/developer/sharepoint-2010/aa544500(v=office.14)).

 Możesz również dostosować kroki wdrażania na komputerze deweloperskim. Aby uzyskać więcej informacji, zobacz [wdrażanie, publikowanie i uaktualnianie pakietów rozwiązania SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).

## <a name="deploy-files-in-sharepoint-solutions"></a>Wdrażanie plików w rozwiązaniach SharePoint
 Zazwyczaj podczas dodawania elementu projektu programu SharePoint do rozwiązania programu SharePoint są uwzględniane wszystkie wymagane pliki. Pliki, które mogą być kompilowane (pliki kodu), są wbudowane w zestaw wyjściowy rozwiązania. Jednak może być również konieczne dodanie plików innych niż nadawać, na przykład plików *XML*, *txt* lub zasobów, do projektu programu SharePoint. Te pliki nie są automatycznie spakowane w rozwiązaniu. Aby upewnić się, że są one spakowane, Dodaj pliki do zamapowanego folderu lub do elementu projektu programu SharePoint.

 Pliki dodane do zamapowanych folderów są automatycznie kopiowane do gałęzi programu SharePoint po wdrożeniu rozwiązania. Pliki dodane do elementu projektu programu SharePoint są wdrażane w lokalizacji określonej we właściwości **lokalizacji wdrożenia** dla każdego pliku, który jest częściowo ustawiony na podstawie właściwości **typ wdrożenia** . Domyślnie wartość właściwości **typ wdrożenia** to **NoDeployment**, co oznacza, że plik nie jest wdrażany wraz z rozwiązaniem. Należy ustawić inną wartość właściwości, aby dołączyć plik do pakietu.

 Na przykład, aby dodać plik *XML* do projektu programu SharePoint, wykonaj jedną z następujących czynności:

- Dodaj zamapowany folder "Layouts" programu SharePoint do projektu. Powoduje to utworzenie w **Eksplorator rozwiązań** folderu o nazwie **Layouts** , który ma podfolder dla projektu. Dodaj plik *XML* do nowego podfolderu. Domyślnie plik jest wdrażany w systemie plików programu SharePoint w obszarze *.. \\\TEMPLATE\LAYOUTS \<Folder Name>*. Aby uzyskać informacje o sposobach dodawania zamapowanych folderów, zobacz [How to: Add and Remove zamapowany Folders](../sharepoint/how-to-add-and-remove-mapped-folders.md).

- Dodaj plik *XML* do folderu elementu projektu programu SharePoint, a następnie zmień właściwość **typ wdrożenia** pliku *XML* z **NoDeployment** na inne ustawienie, takie jak **RootFile** lub **elementu**. Odpowiednie ustawienie **typu wdrożenia** zależy od pliku i projektu. Aby uzyskać więcej informacji na temat ustawień właściwości **typu wdrożenia** , zobacz [opracowywanie rozwiązań programu SharePoint](../sharepoint/developing-sharepoint-solutions.md).

  Jeśli dodany plik nie dotyczy żadnego konkretnego projektu w rozwiązaniu, można dodać do rozwiązania pusty projekt programu SharePoint, a następnie dodać do niego dodatkowe pliki. Inną alternatywą dla wdrażania plików w programie SharePoint, szczególnie w odniesieniu do bazy danych zawartości, jest dodanie modułu do projektu, a następnie dodanie plików do modułu. Aby uzyskać więcej informacji, zobacz [używanie modułów do dołączania plików w rozwiązaniu](../sharepoint/using-modules-to-include-files-in-the-solution.md).

## <a name="see-also"></a>Zobacz też
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
