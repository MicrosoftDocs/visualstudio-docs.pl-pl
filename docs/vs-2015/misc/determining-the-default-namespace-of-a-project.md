---
title: Określanie domyślnej przestrzeni nazw projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d58c8986922c30192d6300a623a635b24c34ed5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705775"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Określanie domyślnej przestrzeni nazw projektu
W przypadku [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , jeśli `CustomToolNamespace` Właściwość jest ustawiona w pliku wejściowym, wartość jest `CustomToolNamespace` wartością domyślnego parametru przestrzeni nazw przekazaną do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metody. W przeciwnym razie `wszDefaultNamespace` parametr przeszedł do `Generate` jest zawsze równy głównej przestrzeni nazw. Aby uzyskać więcej informacji na temat przestrzeni nazw, zobacz [słowa kluczowe przestrzeni nazw](https://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] używa przestrzeni nazw opartych na folderach. Oznacza to, że przestrzeń nazw składa się z głównej przestrzeni nazw oraz nazw wszystkich folderów zawierających narzędzie niestandardowe. Nazwa każdego folderu jest konwertowana na prawidłowy identyfikator, a okresy oddzielają wszystkie nazwy. Na przykład, jeśli plik wejściowy jest FolderA\FolderB\FolderC\MyInput.txt, a główna przestrzeń nazw to CL9, obliczona domyślna przestrzeń nazw to **CL9. Folder. FolderB. FolderC**.  
  
 Wyjątek od tej reguły występuje, gdy łańcuch hierarchii zawiera folder odwołania sieci Web. Na przykład jeśli:  
  
- FolderC były folderem odwołań do sieci Web, przestrzeń nazw byłaby **CL9. FolderC**.  
  
- FolderB były folderem odwołań do sieci Web, przestrzeń nazw byłaby **CL9. FolderB. FolderC**.  
  
  Oznacza to, że przestrzeń nazw używa następującego formatu:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie generatorów pojedynczych plików](../extensibility/internals/implementing-single-file-generators.md)   
 [Rejestrowanie generatorów pojedynczych plików](../extensibility/internals/registering-single-file-generators.md)   
 [Udostępnianie typów dla projektantów wizualnych](../extensibility/internals/exposing-types-to-visual-designers.md)