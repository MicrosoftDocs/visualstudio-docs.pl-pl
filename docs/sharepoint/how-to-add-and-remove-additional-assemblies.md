---
title: 'Instrukcje: Dodawanie i usuwanie zestawów dodatkowych | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: fa25413a40c9b2333acbaba96d55008dbcebfd39
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967033"
---
# <a name="how-to-add-and-remove-additional-assemblies"></a>Instrukcje: Dodawanie i usuwanie zestawów dodatkowych
  Jeśli pakiet programu SharePoint jest zależna od innych zestawów w celu funkcji lub dane, możesz dodać zestawy, do rozwiązania pakietu (wsp). W ten sposób zapewnia, że zainstalowanie zestawów niestandardowych przy użyciu pakietu programu SharePoint server.

 Można dodawać i zmieniać bezpiecznych kontrolek i pliki zasobów klasy skojarzone z zestawów.

## <a name="add-additional-assemblies-safe-controls-and-class-resources"></a>Dodawanie dodatkowych zestawów, bezpieczne kontrolki i zasoby klasy
 Możesz dodać dodatkowe zestawy do pakietu rozwiązania programu SharePoint. Dodatkowe zestawy w trybie piaskownicy rozwiązań wdrożyć do globalnej pamięci podręcznej, ale elementów projektu programu SharePoint w trybie piaskownicy rozwiązań są dodawane do bazy danych zawartości. Bezpieczne kontrolki i zasoby klasy można również dodać do tych dodatkowych zestawów. Aby uzyskać więcej informacji na temat bezpiecznych kontrolek, zobacz [dostarczanie pakowania i informacje o wdrożeniu w elementach projektu](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) lub "Tworzenie SafeControl — wpis" [wdrażania składników Web Part w SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).

#### <a name="to-add-an-existing-assembly"></a>Aby dodać istniejący zestaw

1. Otwórz **pakietu projektanta**. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Wybierz **zaawansowane** kartę.

3. Wybierz **Dodaj** przycisk, a następnie wybierz **Dodaj istniejący zestaw** z listy.

     **Dodaj istniejący zestaw** pojawi się okno dialogowe.

4. Wybierz przycisk wielokropka (![elipsy projektanta Mobile ASP.NET](../sharepoint/media/mwellipsis.gif "elipsy projektanta Mobile ASP.NET")), a następnie wybierz zestaw, który chcesz dodać. Firma Microsoft zaleca, za pomocą ścieżki względnej do wybranego zestawu dla celów przenoszenia.

5. Aby uzyskać **cel wdrożenia**, wybierz **GlobalAssemblyCache** przycisk opcji, aby wdrożyć zestaw do globalnej pamięci podręcznej, lub wybierz **WebApplication** — opcja przycisk, aby wdrożyć zestaw do folderu aplikacji sieci Web na serwerze, na którym uruchomiony jest SharePoint.

#### <a name="to-add-an-assembly-from-project-output"></a>Aby dodać zestaw z danych wyjściowych projektu

1. Otwórz **pakietu projektanta**.

     Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Wybierz **zaawansowane** kartę.

3. Wybierz **Dodaj** przycisk, a następnie wybierz **Dodawanie zestawu z danych wyjściowych projektu** z listy.

     **Dodawanie zestawu z danych wyjściowych projektu** pojawi się okno dialogowe.

4. W **projekt źródłowy** listy, a następnie wybierz projekt źródłowy, który chcesz dodać.

5. Aby uzyskać **cel wdrożenia**, wybierz **GlobalAssemblyCache** przycisk opcji, aby wdrożyć zestaw do globalnej pamięci podręcznej, lub wybierz **WebApplication** — opcja przycisk, aby wdrożyć zestaw do folderu aplikacji sieci Web na serwerze, na którym uruchomiony jest SharePoint.

#### <a name="to-add-a-safe-control"></a>Aby dodać kontrolkę bezpieczne

1. Otwórz **edycji istniejący zestaw** okno dialogowe. Aby to zrobić, otwórz projektanta pakietu, wybierz **zaawansowane** karty, wybierz zestaw, a następnie wybierz **Edytuj** przycisku.

2. W **bezpiecznych kontrolek** okienku wybierz **kliknij tutaj, aby dodać nowy element** przycisku.

3. W **nazwy zestawu** kolumny, wprowadź nazwę zestawu.

4. W **Namespace** kolumny, wprowadź nazwę przestrzeni nazw dla bezpiecznej kontrolki.

5. W **nazwy typu** kolumny, wprowadź nazwę typu.

#### <a name="to-add-a-class-resource"></a>Aby dodać zasób klasy

1. Otwórz **edycji istniejący zestaw** okno dialogowe. Aby to zrobić, otwórz projektanta pakietu, wybierz **zaawansowane** karty, wybierz zestaw, a następnie wybierz **Edytuj** przycisku.

2. W **zasoby klasy** okienku wybierz **kliknij tutaj, aby dodać nowy element** przycisku.

3. W **nazwy pliku** kolumny, wybierz przycisk wielokropka (![elipsy projektanta Mobile ASP.NET](../sharepoint/media/mwellipsis.gif "elipsy projektanta Mobile ASP.NET")) i wybierz zasób klasy, które chcesz dodać.

## <a name="delete-custom-assemblies"></a>Usuwanie zestawów niestandardowych
 Usuwanie zestawów z pakietu programu SharePoint lub usunąć bezpiecznych kontrolek i zasoby klasy z istniejących zestawów.

#### <a name="to-delete-an-existing-assembly"></a>Aby usunąć istniejący zestaw

1. Otwórz **pakietu projektanta**. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie pakietu rozwiązania SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Wybierz **zaawansowane** kartę.

3. W **dodatkowe zestawy** okienku wybierz zestaw niestandardowy, który chcesz usunąć.

4. Wybierz **Usuń** przycisku.

#### <a name="to-delete-a-safe-control-for-an-assembly"></a>Aby usunąć bezpiecznej kontrolki dla zestawu

1. Otwórz **edycji istniejący zestaw** okno dialogowe. Aby to zrobić, otwórz projektanta pakietu, wybierz **zaawansowane** karty, wybierz zestaw, a następnie wybierz **Edytuj** przycisku.

2. Wybierz bezpiecznej kontrolki, które chcesz usunąć.

3. Naciśnij klawisz Delete.

#### <a name="to-delete-a-class-resource-for-an-assembly"></a>Aby usunąć zasób klasy dla zestawu

1. Otwórz **edycji istniejący zestaw** okno dialogowe. Aby to zrobić, otwórz projektanta pakietu, wybierz **zaawansowane** karty, wybierz zestaw, a następnie wybierz **Edytuj** przycisku.

2. Wybierz zasób klasy, która ma zostać usunięty.

3. Naciśnij klawisz Delete.

## <a name="see-also"></a>Zobacz także
- [Tworzenie funkcji SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Instrukcje: Dostosowywanie funkcji SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Instrukcje: Dodawanie i usuwanie elementów do funkcji SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
