---
title: Określanie Namespace domyślnego projektu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 0bc5cba2651f447e36491c641e9b0d05f728e5c7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54791763"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Określanie Namespace domyślnego projektu
Dla [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], jeśli `CustomToolNamespace` właściwość jest ustawiona w pliku wejściowego, a następnie wartość `CustomToolNamespace` staje się wartością domyślnego parametru przestrzeni nazw, przekazana do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> metody. W przeciwnym razie `wszDefaultNamespace` parametr przekazany do `Generate` jest zawsze równa głównej przestrzeni nazw. Aby uzyskać więcej informacji na temat przestrzenie nazw, zobacz [słowa kluczowe Namespace](http://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] używa przestrzeni nazw opartych na folder. Oznacza to, że przestrzeń nazw składa się z głównego obszaru nazw, a także nazwy dowolnego folderu zawierającego narzędzie niestandardowe. Każda nazwa folderu jest konwertowana na prawidłowy identyfikator i okresy oddzielić wszystkie nazwy. Na przykład, jeśli plik wejściowy jest FolderA\FolderB\FolderC\MyInput.txt oraz główna przestrzeń nazw jest CL9 obliczanej domyślny obszar nazw będzie **CL9. FolderA.FolderB.FolderC**.  
  
 Wyjątkiem od tej reguły występuje, gdy łańcucha hierarchii zawiera folder odwołania sieci Web. Na przykład jeśli:  
  
- FolderC były folder odwołania sieci Web, przestrzeń nazw będzie **CL9. FolderC**.  
  
- FolderB były folder odwołania sieci Web, przestrzeń nazw będzie **CL9. FolderB.FolderC**.  
  
  Oznacza to, że przestrzeń nazw posługuje się następującym formatem:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie generatorów jednoplikowych](../extensibility/internals/implementing-single-file-generators.md)   
 [Rejestrowanie generatorów jednoplikowych](../extensibility/internals/registering-single-file-generators.md)   
 [Udostępnianie typów dla projektantów wizualnych](../extensibility/internals/exposing-types-to-visual-designers.md)