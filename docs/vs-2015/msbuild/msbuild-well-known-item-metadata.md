---
title: Metadane dobrze znanego elementu MSBuild | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648942"
---
# <a name="msbuild-well-known-item-metadata"></a>Metadane dobrze znanego elementu MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Poniższa tabela opisuje metadane przypisywane do każdego elementu przy utworzeniu. W każdym przykładzie użyto następującej deklaracji elementu dołączenie pliku `C:\MyProject\Source\Program.cs` w projekcie.  
  
```  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Metadane elementu|Opis|  
|-------------------|-----------------|  
|%(FullPath)|Zawiera pełną ścieżkę elementu. Na przykład:<br /><br /> `C:\MyProject\Source\Program.cs`|  
|%(RootDir)|Zawiera katalog główny elementu. Na przykład:<br /><br /> `C:\`|  
|%(Filename)|Zawiera nazwę pliku bez rozszerzenia elementu. Na przykład:<br /><br /> `Program`|  
|%(Extension)|Zawiera rozszerzenie nazwy pliku elementu. Na przykład:<br /><br /> `.cs`|  
|%(RelativeDir)|Zawiera ścieżkę określoną w `Include` atrybutu do końcowej kreski ułamkowej odwróconej (\\). Na przykład:<br /><br /> `Source\`|  
|%(Directory)|Zawiera katalog elementu, bez katalogu głównego. Na przykład:<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|Jeśli `Include` atrybut zawiera symbol wieloznaczny \* \*, te metadane określają część ścieżki, która zastępuje symbol wieloznaczny. Aby uzyskać więcej informacji na temat symboli wieloznacznych, zobacz [jak: Wybieranie plików do kompilacji](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Jeśli folder *C:\MySolution\MyProject\Source\\*  zawiera plik Program.cs, a jeśli plik projektu zawiera ten element:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> następnie wartość `%(MyItem.RecursiveDir)` będzie *MySolution\MyProject\Source\\* .|  
|%(Identity)|Element określony w `Include` atrybutu... Na przykład:<br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|Zawiera sygnaturę czasową od czasu, gdy zmodyfikowano element. Na przykład:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Zawiera sygnaturę czasową od utworzenia elementu. Na przykład:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Zawiera sygnaturę czasową od czasu, gdy uzyskano dostęp do elementu.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy](../msbuild/msbuild-items.md)   
 [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
