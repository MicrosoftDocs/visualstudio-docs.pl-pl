---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ed60fb5262a6af07966ff974b8535ae299f3fc51
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861416"
---
# <a name="vsg_nodefault_instance"></a>VSG_NODEFAULT_INSTANCE
Definiuje przez jego obecność, niezależnie od tego, czy jest to domyślne wystąpienie klasy [klasy VsgDbg](vsgdbg-class.md) , która zapewnia interfejs przechwytywania programowego — jest dostarczany.

## <a name="syntax"></a>Składnia

```C++
#define VSG_NODEFAULT_INSTANCE
```

## <a name="value"></a>Wartość
 Symbol preprocesora, który jest obecny w obecności lub nieobecności, określa, czy `VsgDbg` jest udostępniane wystąpienie domyślne klasy. Jeśli ten symbol jest zdefiniowany, nie zostanie podane żadne domyślne wystąpienie `VsgDbg` klasy; w przeciwnym razie wystąpienie domyślne jest dostarczane i inicjowane przed uruchomieniem programu.

 Interfejs przechwytywania programistycznego jest dostarczany za pomocą wskaźnika, który ma zakres globalny, `g_pVsgDbg` .

```cpp
VsgDbg *g_pVsgDbg;
```

## <a name="remarks"></a>Uwagi
 Wystąpienie domyślne jest często wystarczające, ale do korzystania z interfejsu przechwycenia programistycznego w bibliotece DLL, gdy urządzenie D3D zostało utworzone poza tą biblioteką DLL, należy utworzyć własne wystąpienie klasy i zarządzać nim `VsgDbg` . Jeśli zarządzasz własnym interfejsem do interfejsu API przechwytywania programistycznego w ten sposób, Wyłącz domyślne wystąpienie przez zdefiniowanie, `VSG_NODEFAULT_INSTANCE` Aby uniknąć narzutu.

 Jeśli wystąpienie domyślne nie jest wyłączone, zostanie automatycznie zainicjowane przed uruchomieniem programu i zostanie automatycznie zniszczone po zakończeniu działania programu. Nie jest konieczne jawne inicjowanie lub inicjowanie tego wystąpienia.

 Aby wyłączyć domyślne wystąpienie, należy zdefiniować `VSG_NODEFAULT_INSTANCE` przed dołączeniem do `vsgcapture.h` programu.

## <a name="example"></a>Przykład
 Ten przykład pokazuje, jak wyłączyć domyślne wystąpienie:

```cpp
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h
#define VSG_NODEFAULT_INSTANCE

#include <vsgcapture.h>
```
