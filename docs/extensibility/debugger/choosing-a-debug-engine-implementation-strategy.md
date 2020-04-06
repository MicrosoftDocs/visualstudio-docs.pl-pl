---
title: Wybór strategii wdrażania aparatu debugowania | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05e66975a2d41108d3d9fb469da9e4a36a10d8d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739129"
---
# <a name="choose-a-debug-engine-implementation-strategy"></a>Wybieranie strategii wdrażania aparatu debugowania
Użyj architektury wykonawczej, aby określić strategię implementacji aparatu debugowania (DE). Można utworzyć aparat debugowania w procesie do programu, który debugujesz. Tworzenie aparatu debugowania w procesie do Menedżera debugowania sesji programu Visual Studio (SDM). Lub utworzyć aparat debugowania poza procesem do obu z nich. Poniższe wytyczne powinny pomóc wybrać jedną z tych trzech strategii.

## <a name="guidelines"></a>Wytyczne
 Chociaż jest możliwe dla DE być poza procesem zarówno SDM i program, który debugujesz, zazwyczaj nie ma powodu, aby to zrobić. Wywołania między granicami procesu są stosunkowo powolne.

 Aparaty debugowania są już przewidziane dla środowiska wykonywania natywnego Win32 i dla środowiska wykonywania języka wspólnego. Jeśli trzeba zastąpić DE dla obu środowisk, należy utworzyć DE w procesie z SDM.

 W przeciwnym razie można utworzyć DE w procesie do SDM lub w trakcie do programu, który debugujesz. Należy wziąć pod uwagę, czy oceniający wyrażenie DE wymaga częstego dostępu do magazynu symboli programu. Lub, jeśli magazyn symboli można załadować do pamięci w celu szybkiego dostępu. Należy również wziąć pod uwagę następujące podejścia:

- Jeśli nie ma wielu wywołań między oceniającego wyrażenie i magazynu symboli lub jeśli magazyn symboli mogą być odczytywane w przestrzeni pamięci SDM, należy utworzyć DE w procesie do SDM. Należy zwrócić clsid aparatu debugowania do SDM po podłączeniu do programu. SDM używa tego identyfikatora CLSID do utworzenia wystąpienia w procesie DE.

- Jeśli DE musi wywołać program, aby uzyskać dostęp do magazynu symboli, należy utworzyć DE w procesie z programem. W takim przypadku program tworzy wystąpienie DE.

## <a name="see-also"></a>Zobacz też
- [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
