---
title: SGen — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3be3aa5426c2d1283b8b4cded51cc9c2772642ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682081"
---
# <a name="sgen-task"></a>SGen — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tworzy zestaw serializacji XML dla typów w określonym zestawie. To zadanie otacza narzędzie XML Serializer Generator (Sgen.exe). Aby uzyskać więcej informacji, zobacz [narzędzie XML Serializer Generator (Sgen.exe)](https://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `SGen` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`BuildAssemblyName`|Wymagany parametr interfejsu `String`.<br /><br /> Zestaw, dla którego ma zostać wygenerowany kod serializacji.|  
|`BuildAssemblyPath`|Wymagany parametr interfejsu `String`.<br /><br /> Ścieżka do zestawu, dla którego ma zostać wygenerowany kod serializacji.|  
|`DelaySign`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , określa, że chcesz użyć w pełni podpisanego zestawu. Jeśli `false` , określa, że chcesz umieścić klucz publiczny w zestawie.<br /><br /> Ten parametr nie ma żadnego efektu, chyba że jest używany z `KeyFile` `KeyContainer` parametrem or.|  
|`KeyContainer`|Opcjonalny `String` parametr.<br /><br /> Określa kontener zawierający parę kluczy. Spowoduje to podpisywanie zestawu przez wstawienie klucza publicznego do manifestu zestawu. Następnie zadanie spowoduje podpisywanie końcowego zestawu przy użyciu klucza prywatnego.|  
|`KeyFile`|Opcjonalny `String` parametr.<br /><br /> Określa parę kluczy lub klucz publiczny do użycia w celu podpisania zestawu. Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego.|  
|`Platform`|Opcjonalny `String` parametr.<br /><br /> Pobiera lub ustawia platformę kompilatora używaną do generowania zestawu wyjściowego. Ten parametr może mieć wartość `x86` , `x64` , lub `anycpu` . Wartość domyślna to `anycpu`.|  
|`References`|Opcjonalny `String[]` parametr.<br /><br /> Określa zestawy, które są określone przez typy wymagające serializacji XML.|  
|`SdkToolsPath`|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak resgen.exe.|  
|`SerializationAssembly`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera wygenerowany zestaw serializacji.|  
|`SerializationAssemblyName`|Opcjonalny `String` parametr.<br /><br /> Określa nazwę wygenerowanego zestawu serializacji.|  
|`ShouldGenerateSerializer`|Wymagany parametr interfejsu `Boolean`.<br /><br /> Jeśli `true` zadanie Sgen powinno generować zestaw serializacji.|  
|`Timeout`|Opcjonalny `Int32` parametr.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue` , co oznacza, że nie ma limitu czasu.|  
|`ToolPath`|Opcjonalny `String` parametr.<br /><br /> Określa lokalizację, z której zadanie będzie ładować podstawowy plik wykonywalny (sgen.exe). Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK odpowiadającej wersji platformy, która jest uruchomiona [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
|`Types`|Opcjonalny `String[]` parametr.<br /><br /> Pobiera lub ustawia listę konkretnych typów, dla których ma zostać wygenerowany kod serializacji. SGen generuje kod serializacji tylko dla tych typów.|  
|`UseProxyTypes`|Wymagany parametr interfejsu `Boolean`.<br /><br /> Jeśli `true` zadanie SGen generuje kod serializacji tylko dla typów serwera proxy usługi sieci Web XML.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
