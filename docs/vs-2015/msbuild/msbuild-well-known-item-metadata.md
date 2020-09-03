---
title: Metadane dobrze znanego elementu MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1bb2e53102221194dc829df162c44bbf04378b28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154084"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadane dobrze znanego elementu MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W poniższej tabeli opisano metadane przypisane do każdego elementu podczas tworzenia. W każdym przykładzie następująca deklaracja elementu została użyta w celu dołączenia pliku do `C:\MyProject\Source\Program.cs` projektu.  
  
```  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Metadane elementu|Opis|  
|-------------------|-----------------|  
|% (FullPath)|Zawiera pełną ścieżkę do elementu. Na przykład:<br /><br /> `C:\MyProject\Source\Program.cs`|  
|% (RootDir)|Zawiera katalog główny elementu. Na przykład:<br /><br /> `C:\`|  
|% (Filename)|Zawiera nazwę pliku elementu, bez rozszerzenia. Na przykład:<br /><br /> `Program`|  
|% (Rozszerzenie)|Zawiera rozszerzenie nazwy pliku elementu. Na przykład:<br /><br /> `.cs`|  
|%(RelativeDir)|Zawiera ścieżkę określoną w `Include` atrybucie, do końcowego ukośnika odwrotnego ( \\ ). Na przykład:<br /><br /> `Source\`|  
|% (Katalog)|Zawiera katalog elementu, bez katalogu głównego. Na przykład:<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|Jeśli `Include` atrybut zawiera symbol wieloznaczny \* \* , metadane określają część ścieżki, która zastępuje symbol wieloznaczny. Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [How to: Wybierz pliki do skompilowania](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Jeśli folder *C:\MySolution\MyProject\Source \\ * zawiera plik program.cs, a plik projektu zawiera ten element:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> następnie wartość `%(MyItem.RecursiveDir)` zostałaby * \\ MySolution\MyProject\Source*.|  
|% (Tożsamość)|Element określony w `Include` atrybucie. Na przykład:<br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|Zawiera sygnaturę czasową od ostatniej modyfikacji elementu. Na przykład:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Zawiera sygnaturę czasową od momentu utworzenia elementu. Na przykład:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Zawiera sygnaturę czasową od ostatniego dostępu do elementu.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Zobacz też  
 [Produktów](../msbuild/msbuild-items.md)   
 [Partie](../msbuild/msbuild-batching.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
