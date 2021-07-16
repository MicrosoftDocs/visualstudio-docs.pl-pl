---
description: Określa, czy jest dostarczane domyślne wystąpienie klasy VsgDbg, która udostępnia interfejs przechwytywania programowego.
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 75bb54adb5667f3e8246034eca1075d339755785
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232417"
---
# <a name="vsg_nodefault_instance"></a>VSG_NODEFAULT_INSTANCE
Określa, czy jest dostarczane domyślne wystąpienie klasy [VsgDbg,](vsgdbg-class.md) która udostępnia interfejs przechwytywania programowego.

## <a name="syntax"></a>Składnia

```C++
#define VSG_NODEFAULT_INSTANCE
```

## <a name="value"></a>Wartość
 Symbol preprocesora, który przez jego obecność lub brak określa, czy jest podane domyślne `VsgDbg` wystąpienie klasy. Jeśli ten symbol jest zdefiniowany, nie zostanie podane domyślne wystąpienie klasy. W przeciwnym razie przed rozpoczęciem programu zostanie podane i zainicjowane `VsgDbg` wystąpienie domyślne.

 Interfejs przechwytywania programowego jest dostarczany za pośrednictwem wskaźnika o zakresie globalnym, `g_pVsgDbg` .

```cpp
VsgDbg *g_pVsgDbg;
```

## <a name="remarks"></a>Uwagi
 Wystąpienie domyślne jest często wystarczające, ale aby użyć interfejsu przechwytywania programowego wewnątrz biblioteki DLL, gdy urządzenie D3D zostało utworzone poza biblioteką DLL, należy utworzyć własne wystąpienie klasy i zarządzać `VsgDbg` nim. Jeśli zarządzasz własnym interfejsem interfejsu API przechwytywania programowego w ten sposób, wyłącz wystąpienie domyślne przez zdefiniowanie, `VSG_NODEFAULT_INSTANCE` aby uniknąć narzutu.

 Jeśli domyślne wystąpienie nie jest wyłączone, jest ono automatycznie inicjowane przed rozpoczęciem programu i jest automatycznie niszczone po zakończeniu programu. Nie trzeba jawnie zainicjować ani niezainicjować tego wystąpienia.

 Aby wyłączyć wystąpienie domyślne, należy zdefiniować przed `VSG_NODEFAULT_INSTANCE` dodaniem `vsgcapture.h` do programu.

## <a name="example"></a>Przykład
 W tym przykładzie pokazano, jak wyłączyć wystąpienie domyślne:

```cpp
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h
#define VSG_NODEFAULT_INSTANCE

#include <vsgcapture.h>
```
