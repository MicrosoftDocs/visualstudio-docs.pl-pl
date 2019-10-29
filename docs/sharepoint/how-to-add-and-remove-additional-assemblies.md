---
title: 'Instrukcje: Dodawanie i usuwanie dodatkowych zestawów | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.CustomAssembly
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bdcc1c478bead4df89622a7311b074965cdc0226
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985234"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Instrukcje: Dodawanie i usuwanie dodatkowych zestawów
  Jeśli pakiet programu SharePoint zależy od innych zestawów dla funkcjonalności lub danych, można dodać zestawy do pakietu rozwiązania (. wsp). Dzięki temu serwer programu SharePoint sprawdza, czy zestawy niestandardowe są instalowane z pakietem.

 Możesz również dodawać i zmieniać bezpieczne kontrolki i pliki zasobów klas skojarzone z zestawami.

## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Dodawanie dodatkowych zestawów, bezpiecznych kontroli i zasobów klas
 Możesz dodać dodatkowe zestawy do pakietu rozwiązania programu SharePoint. Dodatkowe zestawy w rozwiązaniu w trybie piaskownicy są wdrażane w globalnej pamięci podręcznej zestawów, ale elementy projektu programu SharePoint w rozwiązaniu w trybie piaskownicy są dodawane do bazy danych zawartości. Możesz również dodać bezpieczne kontrolki i zasoby klas do tych dodatkowych zestawów. Aby uzyskać więcej informacji o bezpiecznych kontrolach, zobacz [udostępnianie informacji o pakowaniu i wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) lub "Tworzenie wpisu SafeControl" w temacie [wdrażanie składniki Web Part w programie SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/cc768621(v=office.14)).

#### <a name="to-add-an-existing-assembly"></a>Aby dodać istniejący zestaw

1. Otwórz **projektanta pakietów**. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Wybierz kartę **Zaawansowane** .

3. Wybierz przycisk **Dodaj** , a następnie wybierz pozycję **Dodaj istniejący zestaw** z listy.

     Zostanie wyświetlone okno dialogowe **Dodawanie istniejącego zestawu** .

4. Wybierz wielokropek (![ASP.net Mobile Designer](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")), a następnie wybierz zestaw, który chcesz dodać. Zalecamy używanie ścieżki względnej do wybranego zestawu do celów przenośności.

5. W przypadku celu **wdrożenia**wybierz przycisk opcji **GlobalAssemblyCache** , aby wdrożyć zestaw w globalnej pamięci podręcznej zestawów, lub wybierz przycisk opcji **WebApplication** , aby wdrożyć zestaw w folderze WebApplication na stronie serwer z uruchomionym programem SharePoint.

#### <a name="to-add-an-assembly-from-project-output"></a>Aby dodać zestaw z danych wyjściowych projektu

1. Otwórz **projektanta pakietów**.

     Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Wybierz kartę **Zaawansowane** .

3. Wybierz przycisk **Dodaj** , a następnie wybierz polecenie **Dodaj zestaw z danych wyjściowych projektu** z listy.

     Zostanie wyświetlone okno dialogowe **Dodawanie zestawu z danych wyjściowych projektu** .

4. Na liście **projekt źródłowy** i wybierz projekt źródłowy, który chcesz dodać.

5. W przypadku celu **wdrożenia**wybierz przycisk opcji **GlobalAssemblyCache** , aby wdrożyć zestaw w globalnej pamięci podręcznej zestawów, lub wybierz przycisk opcji **WebApplication** , aby wdrożyć zestaw w folderze WebApplication na stronie serwer z uruchomionym programem SharePoint.

#### <a name="to-add-a-safe-control"></a>Aby dodać bezpieczną kontrolę

1. Otwórz okno dialogowe **Edytowanie istniejącego zestawu** . Aby to zrobić, Otwórz projektanta pakietów, wybierz kartę **Zaawansowane** , wybierz zestaw, a następnie wybierz przycisk **Edytuj** .

2. W okienku **bezpieczne formanty** wybierz przycisk **kliknij tutaj, aby dodać nowy element** .

3. W kolumnie **Nazwa zestawu** wpisz nazwę zestawu.

4. W kolumnie **przestrzeń nazw** wprowadź nazwę przestrzeni nazw dla bezpiecznej kontroli.

5. W kolumnie **Nazwa typu** wpisz nazwę typu.

#### <a name="to-add-a-class-resource"></a>Aby dodać zasób klasy

1. Otwórz okno dialogowe **Edytowanie istniejącego zestawu** . Aby to zrobić, Otwórz projektanta pakietów, wybierz kartę **Zaawansowane** , wybierz zestaw, a następnie wybierz przycisk **Edytuj** .

2. W okienku **zasoby klasy** wybierz przycisk **kliknij tutaj, aby dodać nowy element** .

3. W kolumnie **Nazwa pliku** wybierz wielokropek (![ASP.net Mobile Designer](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")) i wybierz zasób klasy, który chcesz dodać.

## <a name="delete-custom-assemblies"></a>Usuń zestawy niestandardowe
 Można usuwać zestawy z pakietu programu SharePoint lub usuwać bezpieczne kontrolki i zasoby klas z istniejących zestawów.

#### <a name="to-delete-an-existing-assembly"></a>Aby usunąć istniejący zestaw

1. Otwórz **projektanta pakietów**. Aby uzyskać więcej informacji, zobacz [How to: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Wybierz kartę **Zaawansowane** .

3. W okienku **dodatkowe zestawy** wybierz zestaw niestandardowy, który chcesz usunąć.

4. Wybierz przycisk **Usuń** .

#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Aby usunąć bezpieczną kontrolę nad zestawem

1. Otwórz okno dialogowe **Edytowanie istniejącego zestawu** . Aby to zrobić, Otwórz projektanta pakietów, wybierz kartę **Zaawansowane** , wybierz zestaw, a następnie wybierz przycisk **Edytuj** .

2. Wybierz bezpieczną kontrolę, którą chcesz usunąć.

3. Wybierz klawisz Delete.

#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Aby usunąć zasób klasy dla zestawu

1. Otwórz okno dialogowe **Edytowanie istniejącego zestawu** . Aby to zrobić, Otwórz projektanta pakietów, wybierz kartę **Zaawansowane** , wybierz zestaw, a następnie wybierz przycisk **Edytuj** .

2. Wybierz zasób klasy, który chcesz usunąć.

3. Wybierz klawisz Delete.

## <a name="see-also"></a>Zobacz także
- [Tworzenie funkcji programu SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Instrukcje: Dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Instrukcje: Dodawanie i usuwanie elementów do funkcji programu SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
