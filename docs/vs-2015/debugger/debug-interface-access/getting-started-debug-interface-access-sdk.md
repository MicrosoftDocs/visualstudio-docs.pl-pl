---
title: Wprowadzenie (dostępu do interfejsu debugowania zestawu SDK) | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54759303"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Wprowadzenie (Zestaw SDK dostępu do interfejsu debugowania)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Debugowanie interfejsu dostępu (DIA) zestaw SDK dostarcza z dokumentacją instruktażowe i próbkę, który ilustruje sposób korzystania z interfejsu API DIA. Użyj interfejsów i metod w DIA SDK do tworzenia niestandardowych aplikacji do otwierania plików .pdb i .dbg i wyszukiwanie ich zawartość dla symboli, wartości, atrybuty, adresów i innych informacji o debugowaniu. Ten zestaw SDK udostępnia również tabele odwołań dla właściwości skojarzone z symbole znajdujące się w aplikacji w języku C++.  
  
 Aby najlepiej użyć DIA SDK, należy zapoznać się z następujących czynności:  
  
- Język programowania w języku C++  
  
- Programowania COM.  
  
- Visual Studio zintegrowanego rozwoju środowiska (IDE) do próbki kompilowania  
  
  DIA SDK jest przeważnie instalowany z programem Visual Studio i jego domyślna lokalizacja to *[dysk]* \Program Files\Microsoft 9.0\DIA programu Visual Studio SDK. W ramach instalacji, msdia90.dll, która implementuje DIA SDK, jest automatycznie rejestrowane więc wszystko, co należy zrobić z niego korzystać do uwzględnienia `dia2.h` w programie i link do `diaguids.lib`.  
  
  Nagłówek: include\dia2.h  
  
  Biblioteka: lib\diaguids.lib  
  
  DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Omówienie](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Przeglądy podstawowej architektury DIA.  
  
 [Używanie zapytań dotyczących pliku .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Instrukcje krok po kroku na temat korzystania z interfejsu API DIA pliku .pdb kwerendy.  
  
## <a name="see-also"></a>Zobacz też  
 [Zestaw SDK dostępu do interfejsu debugowania](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
