---
title: Programowanie narzędzi programu Visual Studio dla unity | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62818218"
---
# <a name="program-visual-studio-tools-for-unity"></a>Programowanie za pomocą narzędzi Visual Studio Tools for Unity
W tej sekcji znajdziesz przykłady korzystania z interfejsu API Visual Studio Tools for Unity.

## <a name="examples"></a>Przykłady
 Oto kilka przykładów, które pokazują, jak można używać narzędzi visual studio dla interfejsów API Unity.

### <a name="customize-project-files-created-by-vstu"></a>Dostosowywanie plików projektu utworzonych przez usługę VSTU
 Visual Studio Tools for Unity zapewnia wywołania zwrotnego w stylu Unity podczas generowania pliku projektu. Aby dowiedzieć się, jak zmodyfikować plik projektu za każdym razem, gdy jest on ponowniegenerowany, zobacz [Przykład: Generowanie pliku projektu](../cross-platform/customize-project-files-created-by-vstu.md).

### <a name="share-the-unity-log-callback-with-vstu"></a>Udostępnianie wywołania zwrotnego dziennika Unity za pomocą usługi VSTU
 Narzędzia programu Visual Studio dla unity rejestruje wywołania zwrotnego dziennika z Unity, aby móc przesyłać strumieniowo jego konsoli do programu Visual Studio. Jeśli skrypty edytora również zarejestrować wywołania zwrotnego dziennika z Unity, wywołanie zwrotne VSTU może kolidować z nim. Aby dowiedzieć się, jak udostępnić wywołanie zwrotne dziennika Unity za pomocą usługi VSTU, zobacz [Przykład: Log callback](../cross-platform/share-the-unity-log-callback-with-vstu.md).
