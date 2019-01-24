---
title: Szczegóły środowiska uruchomieniowego kontroli źródła | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb52770557fa37a14040b686dcdfbf345a713a2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54783715"
---
# <a name="source-control-runtime-details"></a>Szczegóły środowiska uruchomieniowego kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Projekt jest dodawany do kontroli źródła, gdy użytkownik dodaje plik w projekcie do kontroli źródła lub za pośrednictwem kontroler automatyzacji, takie jak kreatora. Projekt nie określa wykorzystywany jest pod kontrolą źródła. obsługuje kontroli źródła, ale należy ręcznie dodać do niego.  
  
## <a name="registering-with-a-source-control-package"></a>Rejestrowanie przy użyciu pakietu kontroli źródła  
 Gdy plik w projekcie zostanie dodany do kontroli źródła, środowisko wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> zapewnienie cztery nieprzezroczyste ciągów, które są używane jako plików cookie przez system kontroli źródła. Store tych ciągów w pliku projektu. Te ciągi powinien zostać przekazany do klasy zastępczej kontroli źródła (składnika programu Visual Studio, który zarządza pakietów kontroli kodu źródłowego) przy uruchamianiu tego typu projektu, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>. To z kolei ładuje pakiet kontroli odpowiednie źródłowe i przekazuje wywołanie do jego implementacja obiektu `IVsSccManager2::RegisterSccProject`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)
