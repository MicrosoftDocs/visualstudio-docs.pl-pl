---
title: Programowanie Visual Studio Tools for Unity | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: a5758cb0-e73b-45f5-8cae-c0eb40491026
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 0811445e2dcf985aef7b6449ff3fb86c5ac9a1c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62818218"
---
# <a name="program-visual-studio-tools-for-unity"></a>Programowanie za pomocą narzędzi Visual Studio Tools for Unity
W tej sekcji znajdziesz przykłady dotyczące korzystania z interfejsu API Visual Studio Tools for Unity.

## <a name="examples"></a>Przykłady
 Poniżej przedstawiono kilka przykładów, które pokazują, jak można używać interfejsów API Visual Studio Tools for Unity.

### <a name="customize-project-files-created-by-vstu"></a>Dostosowywanie plików projektu utworzonych przez rozszerzenia VSTU
 Visual Studio Tools for Unity zapewnia wywołanie zwrotne w stylu aparatu Unity podczas generowania pliku projektu. Aby dowiedzieć się, jak można modyfikować plik projektu za każdym razem, zobacz [przykład: generowanie pliku projektu](../cross-platform/customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Udostępnianie wywołania zwrotnego dziennika aparatu Unity z rozszerzenia VSTU
 Visual Studio Tools for Unity rejestruje wywołanie zwrotne dziennika za pomocą aparatu Unity, aby móc przesyłać strumieniowo swoją konsolę do programu Visual Studio. Jeśli skrypty edytora rejestrują także wywołanie zwrotne dziennika za pomocą aparatu Unity, wywołanie zwrotne rozszerzenia VSTU może zakłócać działanie. Aby dowiedzieć się, jak można udostępnić wywołanie zwrotne dziennika aparatu Unity za pomocą rozszerzenia VSTU, zobacz [przykład: wywołanie zwrotne dziennika](../cross-platform/share-the-unity-log-callback-with-vstu.md).
