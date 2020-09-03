---
title: Wprowadzenie (zestaw SDK dostępu do interfejsu debugowania) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54f83f00ed2e99d1541e15092cb3ee0ce9e08952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164171"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Wprowadzenie (Zestaw SDK dostępu do interfejsu debugowania)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zestaw SDK dostępu do interfejsu debugowania (DIA) udostępnia dokumentację z instrukcjami i przykład, który ilustruje sposób korzystania z interfejsu API DIA. Korzystając z interfejsów i metod w DIA SDK, można opracowywać niestandardowe aplikacje, które otwierają pliki. pdb i. dbg i przeszukiwania ich zawartości pod kątem symboli, wartości, atrybutów, adresów i innych informacji o debugowaniu. Ten zestaw SDK zawiera również tabele referencyjne dla właściwości skojarzonych z symbolami znalezionymi w aplikacjach C++.  
  
 Aby najlepiej używać DIA SDK, należy zapoznać się z następującymi kwestiami:  
  
- Język programowania C++  
  
- Programowanie COM  
  
- Zintegrowane środowisko programistyczne (IDE) programu Visual Studio do kompilowania przykładów  
  
  DIA SDK jest zwykle instalowany z programem Visual Studio i jego domyślną lokalizacją jest *[dysk]* \Program Files\Microsoft Visual Studio 9.0 \ DIA SDK. W ramach instalacji msdia90.dll, który implementuje DIA SDK, jest automatycznie rejestrowany, więc wszystko, co należy zrobić, aby użyć go do dołączenia do `dia2.h` programu i połączenia z `diaguids.lib` .  
  
  Nagłówek: include\dia2.h  
  
  Biblioteka: lib\diaguids.lib  
  
  DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Przegląda podstawową architekturę DIA.  
  
 [Używanie zapytań dotyczących pliku .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Zawiera instrukcje krok po kroku dotyczące korzystania z interfejsu API DIA do wykonywania zapytań dotyczących pliku. pdb.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw SDK dostępu do interfejsu debugowania](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
