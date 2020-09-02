---
title: Programowanie Visual Studio Tools for Unity | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
caps.latest.revision: 5
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 469478f05546a32bb890f759d3d00cb447b54d2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145895"
---
# <a name="programming-visual-studio-tools-for-unity"></a>Programowanie dla rozszerzenia Visual Studio Tools for Unity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tej sekcji znajdziesz przykłady dotyczące korzystania z interfejsu API Visual Studio Tools for Unity.  
  
## <a name="examples"></a>Przykłady  
 Poniżej przedstawiono kilka przykładów, które pokazują, jak można używać interfejsów API Visual Studio Tools for Unity.  
  
### <a name="customize-project-files-created-by-vstu"></a>Dostosowywanie plików projektu utworzonych przez rozszerzenia VSTU  
 Visual Studio Tools for Unity zapewnia wywołanie zwrotne w stylu aparatu Unity podczas generowania pliku projektu. Aby dowiedzieć się, jak można modyfikować plik projektu za każdym razem, zobacz [przykład: generowanie pliku projektu](../cross-platform/customize-project-files-created-by-vstu.md).  
  
### <a name="share-the-unity-log-callback-with-vstu"></a>Udostępnianie wywołania zwrotnego dziennika aparatu Unity z rozszerzenia VSTU  
 Visual Studio Tools for Unity rejestruje wywołanie zwrotne dziennika za pomocą aparatu Unity, aby móc przesyłać strumieniowo swoją konsolę do programu Visual Studio. Jeśli skrypty edytora rejestrują także wywołanie zwrotne dziennika za pomocą aparatu Unity, wywołanie zwrotne rozszerzenia VSTU może zakłócać działanie. Aby dowiedzieć się, jak można udostępnić wywołanie zwrotne dziennika aparatu Unity za pomocą rozszerzenia VSTU, zobacz [przykład: wywołanie zwrotne dziennika](../cross-platform/share-the-unity-log-callback-with-vstu.md).
