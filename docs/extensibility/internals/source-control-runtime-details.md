---
title: Szczegóły środowiska uruchomieniowego kontroli źródła | Microsoft Docs
description: Dowiedz się, jak projekt jest dodawany do kontroli źródła, gdy użytkownik dodaje plik do projektu w kontroli źródła lub za pomocą kontrolera automatyzacji.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bbe1e0e915a28412fcfd411e72b6d622e065b8f8
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877978"
---
# <a name="source-control-runtime-details"></a>Szczegóły środowiska uruchomieniowego kontroli kodu źródłowego
Projekt jest dodawany do kontroli źródła, gdy użytkownik dodaje plik w projekcie do kontroli źródła lub za pomocą kontrolera automatyzacji, takiego jak Kreator. Projekt nie jest określony dla siebie, ponieważ jest pod kontrolą źródła; obsługuje kontrolę źródła, ale należy do niej dodać ręcznie.

## <a name="registering-with-a-source-control-package"></a>Rejestrowanie przy użyciu pakietu kontroli źródła
 Gdy plik w projekcie zostanie dodany do kontroli źródła, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> w celu zapewnienia czterech nieprzezroczystych ciągów, które są używane jako pliki cookie przez system kontroli źródła. Przechowaj te ciągi w pliku projektu. Te ciągi powinny być przesyłane do procedury zastępczej kontroli źródła (składnik programu Visual Studio, który zarządza pakietami kontroli źródła) przy uruchamianiu typu projektu przez wywoływanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . To z kolei powoduje załadowanie odpowiedniego pakietu kontroli źródła i przekazanie wywołania do jego implementacji `IVsSccManager2::RegisterSccProject` .

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)
