---
title: Zadanie XSD | Dokumenty firmy Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 217e045a731efa1fe3ba1dda63e89eca685d4b75
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630785"
---
# <a name="xsd-task"></a>XSD — Zadanie

Zawija narzędzie XML Schema Definition *(xsd.exe),* które generuje pliki schematu lub klasy ze źródła.

> [!NOTE]
> Począwszy od programu Visual Studio 2017, obsługa projektu C++ dla *xsd.exe* jest przestarzała. Nadal można używać interfejsów API **programu Microsoft.VisualC.CppCodeProvider,** ręcznie dodając *plik CppCodeProvider.dll* do pliku GAC.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania **XSD.**

- **Dodatkoweopcje**

     Opcjonalny parametr **String.**

     Lista opcji określonych w wierszu polecenia. Na przykład\</ option1>\</ option2\<> / option#>. Ten parametr służy do określania opcji, które nie są reprezentowane przez żaden inny parametr zadania **XSD.**

- **GenerateFromSchema**

  Opcjonalny parametr **String.**

  Określa typy, które są generowane z określonego schematu.

  Określ jedną z następujących wartości, z których każda odpowiada opcji XSD.

  - **klasy** - **/klasy**

  - **zestaw danych** - **/zestaw danych**

- **Język**

     Opcjonalny parametr **String.**

     Określa język programowania używany dla wygenerowanego kodu.

     Wybierz z **CS** (C#, który jest domyślny), **VB** (Visual Basic) lub **JS** (JScript). Można również określić w pełni kwalifikowaną `System.CodeDom.Compiler.CodeDomProvider Class`nazwę dla klasy, która implementuje .

- **Namespace**

     Opcjonalny parametr **String.**

     Określa przestrzeń nazw czasu wykonywania wygenerowany typów.

- **Źródeł**

     Wymagany parametr interfejsu `ITaskItem[]`.

     Definiuje tablicę elementów pliku źródłowego MSBuild, które mogą być używane i emitowane przez zadania.

- **SuppressStartupBanner (SuppressStartupBanner)**

     Opcjonalny parametr **logiczny.**

     Jeśli `true`program Zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji po uruchomieniu zadania.

- **TrackerLogDirectory (TrackerLogDirectory)**

     Opcjonalny parametr **String.**

     Określa katalog dziennika modułu śledzącego.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
