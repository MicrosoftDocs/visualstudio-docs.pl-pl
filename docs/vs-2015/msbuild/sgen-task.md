---
title: SGen — zadanie | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2741dc6e3e08f8c7f7ee2e28bcf2d8df1613f10e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647242"
---
# <a name="sgen-task"></a>SGen — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tworzy zestaw serializacji XML dla typów w określonym zestawie. To zadanie opakowuje narzędzie generatora serializatora XML (Sgen.exe). Aby uzyskać więcej informacji, zobacz [narzędzie generatora serializatora XML (Sgen.exe)](http://msdn.microsoft.com/library/cc1d1f1c-fb26-4be9-885a-3fe84c81cec6).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `SGen` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`BuildAssemblyName`|Wymagane `String` parametru.<br /><br /> Zestaw do generowania kodu serializacji.|  
|`BuildAssemblyPath`|Wymagane `String` parametru.<br /><br /> Ścieżka do zestawu do generowania kodu serializacji.|  
|`DelaySign`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, określa, że chcesz, aby podpisać zestaw całkowicie. Jeśli `false`, określa, że chcesz tylko umieścić klucz publiczny w zestawie.<br /><br /> Ten parametr jest ignorowany, chyba że używany z `KeyFile` lub `KeyContainer` parametru.|  
|`KeyContainer`|Opcjonalnie `String` parametru.<br /><br /> Określa kontener zawierający parę kluczy. Zestaw zostanie podpisany przez wstawienie klucza publicznego do manifestu zestawu. Zadanie następnie podpisze ostateczny zestaw przy użyciu klucza prywatnego.|  
|`KeyFile`|Opcjonalnie `String` parametru.<br /><br /> Określa pary kluczy lub klucz publiczny używany do podpisywania zestawu. Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego.|  
|`Platform`|Opcjonalnie `String` parametru.<br /><br /> Pobiera lub ustawia platformy kompilatora, używane do generowania zestawu wyjściowego. Ten parametr może mieć wartość `x86`, `x64`, lub `anycpu`. Wartość domyślna to `anycpu`.|  
|`References`|Opcjonalnie `String[]` parametru.<br /><br /> Określa zestawy, które są określone przez typy wymagające serializacji XML.|  
|`SdkToolsPath`|Opcjonalnie `String` parametru.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak resgen.exe.|  
|`SerializationAssembly`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Zawiera zestaw wygenerowany serializacji.|  
|`SerializationAssemblyName`|Opcjonalnie `String` parametru.<br /><br /> Określa nazwę zestawu wygenerowanego serializacji.|  
|`ShouldGenerateSerializer`|Wymagane `Boolean` parametru.<br /><br /> Jeśli `true`, SGen — zadanie powinien wygenerować zestawu serializacji.|  
|`Timeout`|Opcjonalnie `Int32` parametru.<br /><br /> Określa ilość czasu w milisekundach, po których zostanie zakończony wykonywalnego zadania podrzędnego. Wartość domyślna to `Int.MaxValue`, wskazujący, że nie okres limitu czasu.|  
|`ToolPath`|Opcjonalnie `String` parametru.<br /><br /> Określa lokalizację, z którym zadanie załaduje podstawowego pliku wykonywalnego (sgen.exe). Jeśli nie określono tego parametru, zadanie używa ścieżki instalacji zestawu SDK odpowiadający wersję framework, na którym działa [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|`Types`|Opcjonalnie `String[]` parametru.<br /><br /> Pobiera lub ustawia listę określonych typów do generowania kodu serializacji. SGen wygeneruje kod serializacji tylko dla tych typów.|  
|`UseProxyTypes`|Wymagane `Boolean` parametru.<br /><br /> Jeśli `true`, SGen — zadanie generuje kod serializacji tylko dla typów serwera proxy usług sieci Web XML.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [tooltaskextension — klasa bazowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
