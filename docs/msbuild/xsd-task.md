---
title: Zadanie XSD | Microsoft Docs
description: Dowiedz się, w jaki sposób MSBuild używa zadania XSD do pakowania narzędzia definicji schematu XML xsd.exe, które generuje pliki schematu lub klasy ze źródła.
ms.custom: SEO-VS-2020
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.xsd
- VC.Project.VCXMLDataGeneratorTool.Namespace
- VC.Project.VCXMLDataGeneratorTool.GenerateFromSchema
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XSD task (MSBuild (C++))
- MSBuild (C++), XSD task
ms.assetid: 15c99f5c-7124-4bbc-bc03-70c7bcce8893
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7227fff5dd4c58e1bce81ef8cad5c32f854abf55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960328"
---
# <a name="xsd-task"></a>XSD — Zadanie

Zawija narzędzie definicji schematu XML (*xsd.exe*), które generuje pliki schematu lub klasy ze źródła.

> [!NOTE]
> Począwszy od programu Visual Studio 2017, obsługa projektu C++ dla *xsd.exe* jest przestarzała. Można nadal używać interfejsów API **Microsoft. VisualC. CppCodeProvider** , ręcznie dodając *CppCodeProvider.dll* do pamięci podręcznej GAC.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **XSD** .

- **AdditionalOptions**

     Opcjonalny parametr **ciągu** .

     Lista opcji określona w wierszu polecenia. Na przykład/ \<option1>  / \<option2>  / \<option#> . Użyj tego parametru, aby określić opcje, które nie są reprezentowane przez żaden inny parametr zadania **XSD** .

- **GenerateFromSchema**

  Opcjonalny parametr **ciągu** .

  Określa typy, które są generowane na podstawie określonego schematu.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji XSD.

  - **klasy**  -  **/Classes**

  - **zestaw danych**  -  **/DataSet**

- **Język**

     Opcjonalny parametr **ciągu** .

     Określa język programowania, który ma być używany dla wygenerowanego kodu.

     Wybierz pozycję z **CS** (C#, która jest domyślna), **VB** (Visual Basic) lub **js** (JScript). Można również określić w pełni kwalifikowaną nazwę dla klasy implementującej `System.CodeDom.Compiler.CodeDomProvider Class` .

- **Przestrzeń nazw**

     Opcjonalny parametr **ciągu** .

     Określa przestrzeń nazw czasu wykonywania wygenerowany typów.

- **Źródła**

     Wymagany parametr interfejsu `ITaskItem[]`.

     Definiuje tablicę elementów plików źródłowych MSBuild, które mogą być używane i emitowane przez zadania.

- **SuppressStartupBanner**

     Opcjonalny parametr **logiczny** .

     Jeśli `true` , program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.

- **Katalog trackerlogdirectory**

     Opcjonalny parametr **ciągu** .

     Określa katalog dziennika śledzenia.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
