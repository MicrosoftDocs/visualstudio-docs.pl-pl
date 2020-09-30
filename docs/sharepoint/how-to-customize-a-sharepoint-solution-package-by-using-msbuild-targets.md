---
title: Dostosowywanie pakietu rozwiązania SharePoint przy użyciu elementów docelowych programu MSBuild
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 9845f755d184c18b6b5ade4c5504e393edae7b00
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585813"
---
# <a name="how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets"></a>Instrukcje: Dostosowywanie pakietu rozwiązania SharePoint przy użyciu elementów docelowych MSBuild
  Za pomocą obiektów docelowych programu MSBuild w wierszu polecenia można dostosować sposób, w jaki program Visual Studio tworzy pliki pakietu SharePoint (*wsp*). Na przykład można dostosować właściwości programu MSBuild, aby zmienić katalog pośredni pakietu i grupy elementów MSBuild, które określają pliki wyliczane.

## <a name="customize-and-run-msbuild-targets"></a>Dostosowywanie i uruchamianie obiektów docelowych programu MSBuild
 W przypadku dostosowania obiektów docelowych BeforeLayout i AfterLayout można wykonywać zadania przed układem pakietu, takie jak dodawanie, usuwanie lub modyfikowanie plików, które będą spakowane.

#### <a name="to-customize-the-beforelayout-target"></a>Aby dostosować element docelowy BeforeLayout

1. Otwórz Edytor, taki jak Notatnik, a następnie Dodaj następujący kod.

   ```xml
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <Target Name="BeforeLayout">
       <Message Importance="high" Text="In the BeforeLayout Target"></Message>
     </Target>
   </Project>
   ```

    Ten przykład wyświetla komunikat przed opakowaniem tego obiektu docelowego.

2. Nazwij plik **CustomLayout. SharePoint. targets**, a następnie zapisz go w folderze dla projektu programu SharePoint.

3. Otwórz projekt, otwórz jego menu skrótów, a następnie wybierz polecenie **Zwolnij projekt**.

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz **Edytuj** * \<ProjectName> . vbproj* lub **Edytuj** * \<ProjectName> . csproj*.

5. Po `Import` wierszu blisko końca pliku projektu Dodaj następujący wiersz.

   ```xml
   <Import Project="CustomLayout.SharePoint.targets" />
   ```

6. Zapisz i zamknij plik projektu.

7. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Załaduj ponownie projekt**.

   Podczas publikowania projektu, komunikat pojawi się w danych wyjściowych przed rozpoczęciem pakowania.

#### <a name="to-customize-the-afterlayout-target"></a>Aby dostosować element docelowy AfterLayout

1. Na pasku menu wybierz **plik**  >  **Otwórz**  >  **plik**.

2. W oknie dialogowym **Otwórz plik** przejdź do folderu projektu, wybierz plik CustomLayout. Target, a następnie wybierz przycisk **Otwórz** .

3. Tuż przed `</Project>` tagiem Dodaj następujący kod:

   ```xml
   <Target Name="AfterLayout">
     <Message Importance="high" Text="In the AfterLayout Target"></Message>
   </Target>
   ```

    Ten przykład wyświetla komunikat po spakowaniu tego obiektu docelowego.

4. Zapisz i zamknij plik targets.

5. Uruchom ponownie program Visual Studio, a następnie otwórz projekt.

   Po opublikowaniu projektu komunikat BeforeLayout jest wyświetlany przed rozpoczęciem tworzenia pakietu, a po zakończeniu tworzenia pakietu pojawi się komunikat AfterLayout.

## <a name="see-also"></a>Zobacz też
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
