---
title: VSG_NODEFAULT_INSTANCE | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5422cf4899e68a913e6cf15e4923da564859653
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53922576"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
Definiuje przez jego obecność, czy domyślne wystąpienie [VsgDbg, klasa](vsgdbg-class.md) klasy — który zapewnia interfejs przechwycenie programowe — jest dostarczany.  
  
## <a name="syntax"></a>Składnia  
  
```C++  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Wartość  
 Preprocesor symbol przez jego obecności lub braku Określa, czy domyślne wystąpienie `VsgDbg` są dostarczane przez klasy. Jeśli ten symbol jest zdefiniowany, następnie nie domyślne wystąpienie `VsgDbg` klasy jest dostarczana, w przeciwnym razie domyślnego wystąpienia ma być dostarczana i zainicjowany przed uruchomieniem programu.  
  
 Interfejs Przechwytywanie programistyczne jest podana za pomocą wskaźnika, który ma zakres globalny, `g_pVsgDbg`.  
  
```cpp
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślne wystąpienie często jest wystarczająca, ale aby używać interfejsu Przechwytywanie programistyczne wewnątrz biblioteki DLL, gdy urządzenie D3D została utworzona poza tej biblioteki DLL, należy utworzyć i zarządzać wystąpienia programu `VsgDbg` klasy. Jeśli zarządzasz interfejsu do Przechwytywanie programistyczne interfejsu API w ten sposób wyłączyć domyślnego wystąpienia, definiując `VSG_NODEFAULT_INSTANCE` Aby uniknąć zadań.  
  
 Jeśli wystąpienie domyślne nie zostanie wyłączony, automatycznie jest inicjowana przed uruchomień programu i automatycznie jest niszczony, kiedy kończy się program. Nie masz do inicjowania lub jawnie uninitialize tego wystąpienia.  
  
 Aby wyłączyć domyślnego wystąpienia, należy zdefiniować `VSG_NODEFAULT_INSTANCE` przed wprowadzeniem `vsgcapture.h` w programach.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób wyłączania wystąpienie domyślne:  
  
```cpp
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```
