---
title: VSG_NODEFAULT_INSTANCE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b43affa6db83d34d18a3f485a88f41ccde5d22a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804420"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definiuje przez jego obecność, czy domyślne wystąpienie [VsgDbg, klasa](../debugger/vsgdbg-class.md) klasy — który zapewnia interfejs przechwycenie programowe — jest dostarczany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Wartość  
 Preprocesor symbol przez jego obecności lub braku Określa, czy domyślne wystąpienie `VsgDbg` są dostarczane przez klasy. Jeśli ten symbol jest zdefiniowany, następnie nie domyślne wystąpienie `VsgDbg` klasy jest dostarczana, w przeciwnym razie domyślnego wystąpienia ma być dostarczana i zainicjowany przed uruchomieniem programu.  
  
 Interfejs Przechwytywanie programistyczne jest podana za pomocą wskaźnika, który ma zakres globalny, `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślne wystąpienie często jest wystarczająca, ale aby używać interfejsu Przechwytywanie programistyczne wewnątrz biblioteki DLL, gdy urządzenie D3D została utworzona poza tej biblioteki DLL, należy utworzyć i zarządzać wystąpienia programu `VsgDbg` klasy. Jeśli zarządzasz interfejsu do Przechwytywanie programistyczne interfejsu API w ten sposób wyłączyć domyślnego wystąpienia, definiując `VSG_NODEFAULT_INSTANCE` Aby uniknąć zadań.  
  
 Jeśli wystąpienie domyślne nie zostanie wyłączony, automatycznie jest inicjowana przed uruchomień programu i automatycznie jest niszczony, kiedy kończy się program. Nie masz do inicjowania lub jawnie uninitialize tego wystąpienia.  
  
 Aby wyłączyć domyślnego wystąpienia, należy zdefiniować `VSG_NODEFAULT_INSTANCE` przed wprowadzeniem `vsgcapture.h` w programach.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób wyłączania wystąpienie domyślne:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```



