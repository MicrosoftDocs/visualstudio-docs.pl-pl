---
title: Szczegóły środowiska uruchomieniowego kontroli źródła | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d2469bc25fabd9659e09d6ca841ebc44a743cca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723406"
---
# <a name="source-control-runtime-details"></a>Szczegóły środowiska uruchomieniowego kontroli kodu źródłowego
Projekt jest dodawany do kontroli źródła, gdy użytkownik dodaje plik w projekcie do kontroli źródła lub za pomocą kontrolera automatyzacji, takiego jak Kreator. Projekt nie jest określony dla siebie, ponieważ jest pod kontrolą źródła; obsługuje kontrolę źródła, ale należy do niej dodać ręcznie.

## <a name="registering-with-a-source-control-package"></a>Rejestrowanie przy użyciu pakietu kontroli źródła
 Gdy plik w projekcie zostanie dodany do kontroli źródła, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>, aby udostępnić cztery nieprzezroczyste ciągi, które są używane jako pliki cookie przez system kontroli źródła. Przechowaj te ciągi w pliku projektu. Te ciągi powinny być przesyłane do procedury zastępczej kontroli źródła (składnik programu Visual Studio, który zarządza pakietami kontroli źródła) przy uruchamianiu typu projektu przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. To z kolei powoduje załadowanie odpowiedniego pakietu kontroli źródła i przekazanie wywołania do jego implementacji `IVsSccManager2::RegisterSccProject`.

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)