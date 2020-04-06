---
title: Szczegóły środowiska uruchomieniowego kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92ce5e822ec7360b3b1a4010d250a4349443c142
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705039"
---
# <a name="source-control-runtime-details"></a>Szczegóły środowiska uruchomieniowego kontroli kodu źródłowego
Projekt jest dodawany do kontroli źródła, gdy użytkownik dodaje plik w projekcie do kontroli źródła lub za pośrednictwem kontrolera automatyzacji, takiego jak kreator. Projekt nie określa dla siebie, że jest pod kontrolą źródła; obsługuje kontrolę źródła, ale należy dodać do niego ręcznie.

## <a name="registering-with-a-source-control-package"></a>Rejestrowanie się za pomocą pakietu kontroli źródła
 Gdy plik w projekcie jest dodawany do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> kontroli źródła, środowisko wywołuje, aby zapewnić cztery nieprzezroczyste ciągi, które są używane jako pliki cookie przez system kontroli źródła. Przechowuj te ciągi w pliku projektu. Te ciągi powinny być przekazywane do źródła źródła (składnika Visual Studio, który zarządza pakietami kontroli źródła) podczas uruchamiania typu projektu przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. To z kolei ładuje odpowiedni pakiet kontroli źródła i `IVsSccManager2::RegisterSccProject`przekazuje wywołanie do jego implementacji .

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)
