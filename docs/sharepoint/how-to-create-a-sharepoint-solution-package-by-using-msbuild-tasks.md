---
title: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild
description: Dowiedz się, jak kompilować, czyścić i sprawdzać pakiet rozwiązań programu SharePoint (wsp) przy użyciu zadań MSBuild wiersza polecenia na komputerze deweloperskim.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f4c1d2e986b6a810cc568efd9577be87a38fdefb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873544"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Instrukcje: Tworzenie pakietu rozwiązania SharePoint przy użyciu zadań MSBuild
  Można kompilować, czyścić i sprawdzać pakiet programu SharePoint (*. wsp*) przy użyciu zadań MSBuild wiersza polecenia na komputerze deweloperskim. Można również użyć tych poleceń do zautomatyzowania procesu kompilacji przy użyciu Team Foundation Server na komputerze kompilacji.

## <a name="build-a-sharepoint-package"></a>Kompiluj pakiet programu SharePoint

#### <a name="to-build-a-sharepoint-package"></a>Aby skompilować pakiet programu SharePoint

1. W menu **Start** systemu Windows wybierz kolejno pozycje **Wszystkie programy**  >  **akcesoria**  >  **wiersz polecenia**.

2. Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.

3. Wprowadź następujące polecenie, aby utworzyć pakiet dla projektu. Zastąp *ProjectFileName* nazwą projektu.

    ```cmd
    msbuild /t:Package ProjectFileName
    ```

     Na przykład można uruchomić jedno z następujących poleceń w celu spakowania projektu programu SharePoint o nazwie ListDefinition1.

    ```cmd
    msbuild /t:Package ListDefinition1.vbproj
    msbuild /t:Package ListDefinition1.csproj
    ```

## <a name="clean-a-sharepoint-package"></a>Czyszczenie pakietu programu SharePoint

#### <a name="to-clean-a-sharepoint-package"></a>Aby wyczyścić pakiet programu SharePoint

1. Otwórz okno wiersza polecenia.

2. Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.

3. Wprowadź następujące polecenie, aby wyczyścić pakiet dla projektu. Zastąp *ProjectFileName* nazwą projektu.

    ```cmd
    msbuild /t:CleanPackage ProjectFileName
    ```

     Na przykład można uruchomić jedno z następujących poleceń w celu oczyszczenia projektu programu SharePoint o nazwie ListDefinition1.

    ```cmd
    msbuild /t:CleanPackage ListDefinition1.vbproj
    msbuild /t:CleanPackage ListDefinition1.csproj
    ```

## <a name="validate-a-sharepoint-package"></a>Weryfikowanie pakietu programu SharePoint

#### <a name="to-validate-a-sharepoint-package"></a>Aby sprawdzić poprawność pakietu programu SharePoint

1. Otwórz okno wiersza polecenia.

2. Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.

3. Wprowadź następujące polecenie, aby sprawdzić poprawność pakietu dla projektu. Zastąp *ProjectFileName* nazwą projektu.

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     Na przykład można uruchomić jedno z następujących poleceń, aby sprawdzić poprawność projektu programu SharePoint o nazwie ListDefinition1.

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>Ustawianie właściwości w pakiecie programu SharePoint

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Aby ustawić właściwość w pakiecie programu SharePoint

1. Otwórz okno wiersza polecenia.

2. Przejdź do katalogu, w którym znajduje się projekt programu SharePoint.

3. Wprowadź następujące polecenie, aby ustawić właściwość w pakiecie dla projektu. Zastąp wartość *PropertyName* właściwością, która ma zostać ustawiona.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     Na przykład można uruchomić następujące polecenie, aby ustawić poziom ostrzeżeń.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>Zobacz też
- [Tworzenie funkcji programu SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Instrukcje: Dostosowywanie funkcji programu SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Instrukcje: Dodawanie i usuwanie elementów do funkcji programu SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
