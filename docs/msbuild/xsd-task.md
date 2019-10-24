---
title: Zadanie XSD | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec51406aec9aec8981e5517480e4cd07bc80ffb1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748010"
---
# <a name="xsd-task"></a>XSD — Zadanie
Zawija narzędzie definicji schematu XML (*XSD. exe*), które generuje pliki schematu lub klasy ze źródła.

> [!NOTE]
> Począwszy od programu Visual Studio 2017 C++ , obsługa projektu dla pliku *XSD. exe* jest przestarzała. Można nadal używać interfejsów API **Microsoft. VisualC. CppCodeProvider** , ręcznie dodając *CppCodeProvider. dll* do pamięci GAC.

## <a name="parameters"></a>Parametry
 W poniższej tabeli opisano parametry zadania **XSD** .

- **AdditionalOptions**

     Opcjonalny parametr **ciągu** .

     Lista opcji określona w wierszu polecenia. Na przykład/\<option1 >/\<option2 >/\<option # >. Użyj tego parametru, aby określić opcje, które nie są reprezentowane przez żaden inny parametr zadania **XSD** .

- **GenerateFromSchema**

  Opcjonalny parametr **ciągu** .

  Określa typy, które są generowane na podstawie określonego schematu.

  Określ jedną z następujących wartości, z których każdy odpowiada opcji XSD.

  - **klasy**  -  **/Classes**

  - **zestaw danych**  -  **/DataSet**

- **Język**

     Opcjonalny parametr **ciągu** .

     Określa język programowania, który ma być używany dla wygenerowanego kodu.

     Wybierz pozycję z firmyC#cs (czyli domyślnej), **VB** (Visual Basic) lub **js** (JScript). Można również określić w pełni kwalifikowaną nazwę klasy, która implementuje `System.CodeDom.Compiler.CodeDomProvider Class`.

- **Obszaru**

     Opcjonalny parametr **ciągu** .

     Określa przestrzeń nazw czasu wykonywania wygenerowany typów.

- **Źródeł**

     Wymagany `ITaskItem[]` parametr.

     Definiuje tablicę elementów plików źródłowych MSBuild, które mogą być używane i emitowane przez zadania.

- **SuppressStartupBanner**

     Opcjonalny parametr **logiczny** .

     Jeśli `true`, program zapobiega wyświetlaniu komunikatu o prawach autorskich i numerze wersji, gdy zadanie zostanie uruchomione.

- **Katalog trackerlogdirectory**

     Opcjonalny parametr **ciągu** .

     Określa katalog dziennika śledzenia.

## <a name="see-also"></a>Zobacz także
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
