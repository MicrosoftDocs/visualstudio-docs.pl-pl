---
title: VSG_NODEFAULT_INSTANCE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c7d2263642c2ff8a2c36f274d2c7b80745ed845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179480"
---
# <a name="vsg_nodefault_instance"></a>VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiuje przez jego obecność, niezależnie od tego, czy jest to domyślne wystąpienie klasy [klasy VsgDbg](../debugger/vsgdbg-class.md) , która zapewnia interfejs przechwytywania programowego — jest dostarczany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Wartość  
 Symbol preprocesora, który jest obecny w obecności lub nieobecności, określa, czy `VsgDbg` jest udostępniane wystąpienie domyślne klasy. Jeśli ten symbol jest zdefiniowany, nie zostanie podane żadne domyślne wystąpienie `VsgDbg` klasy; w przeciwnym razie wystąpienie domyślne jest dostarczane i inicjowane przed uruchomieniem programu.  
  
 Interfejs przechwytywania programistycznego jest dostarczany za pomocą wskaźnika, który ma zakres globalny, `g_pVsgDbg` .  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie domyślne jest często wystarczające, ale do korzystania z interfejsu przechwycenia programistycznego w bibliotece DLL, gdy urządzenie D3D zostało utworzone poza tą biblioteką DLL, należy utworzyć własne wystąpienie klasy i zarządzać nim `VsgDbg` . Jeśli zarządzasz własnym interfejsem do interfejsu API przechwytywania programistycznego w ten sposób, Wyłącz domyślne wystąpienie przez zdefiniowanie, `VSG_NODEFAULT_INSTANCE` Aby uniknąć narzutu.  
  
 Jeśli wystąpienie domyślne nie jest wyłączone, zostanie automatycznie zainicjowane przed uruchomieniem programu i zostanie automatycznie zniszczone po zakończeniu działania programu. Nie jest konieczne jawne inicjowanie lub inicjowanie tego wystąpienia.  
  
 Aby wyłączyć domyślne wystąpienie, należy zdefiniować `VSG_NODEFAULT_INSTANCE` przed dołączeniem do `vsgcapture.h` programu.  
  
## <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak wyłączyć domyślne wystąpienie:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```
