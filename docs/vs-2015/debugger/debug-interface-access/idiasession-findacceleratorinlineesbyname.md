---
title: IDiaSession::findAcceleratorInlineesByName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b547d38779578ca4fc2fba44effc9b5a6037f4fe
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761832"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zwraca wyliczenie symboli dla ramki wbudowane odpowiadającej nazwie funkcji określone w jednej linii.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 [in] Nazwa funkcji przed wstawianiem do treści do wyszukania.  
  
 `option`  
 [in] Opcje wyszukiwania nazw ma być używany podczas wyszukiwania wbudowanego w ramkach, które odpowiadają `name`. Aby uzyskać więcej informacji, zobacz [namesearchoptions — wyliczenie](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 [out] Wskaźnik do `IDiaEnumSymbols` wskaźnik interfejsu, który jest inicjowany z wynikiem.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta funkcja wyszukuje wersji śródwierszowych tylko w ramach funkcji klasy zastępczej akceleratora. Ignoruje natywnego języka C++ procedury rekordów.  
  
## <a name="see-also"></a>Zobacz też  
 [Idiasession —](../../debugger/debug-interface-access/idiasession.md)   
 [Idiaenumsymbols —](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



