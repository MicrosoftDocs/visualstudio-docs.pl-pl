---
title: BeginCapture | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9edbb52d-ee0b-4cc4-a382-972bcee067d3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9521288b27b1f9b11a2fdb8cbbd613f1a77f857d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72736140"
---
# <a name="begincapture"></a>BeginCapture
Rozpoczyna Interwał przechwytywania, który zakończy się od `EndCapture` .

## <a name="syntax"></a>Składnia

```C++
void BeginCapture();
```

## <a name="remarks"></a>Uwagi
 Interwał przechwytywania zazwyczaj obejmuje podzestaw jednej ramki, na przykład, gdy chcesz przechwytywać informacje graficzne tylko o określonym rodzaju wywołania rysowania. Jeśli Interwał przechwytywania rozciąga się na obecność, zostaną przechwycone dwie ramki informacji graficznych. Pierwsza ramka rozciąga się między wywołaniem `BeginCapture` i wywołaniem metody. druga ramka obejmuje interwał między pierwszym zdarzeniem Direct3D po wywołaniu metody i wywołaniem metody `EndCapture` .

 Aby przechwycić interwał, należy przygotować aplikację do przechwytywania i rejestrowania informacji graficznych — to znaczy, że [Init](init.md) `VsgDbg` przed wywołaniem `BeginCapture` lub `EndCapture` .

## <a name="see-also"></a>Zobacz też
- [EndCapture](endcapture.md)
- [CaptureCurrentFrame](capturecurrentframe.md)