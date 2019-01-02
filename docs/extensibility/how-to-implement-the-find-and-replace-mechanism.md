---
title: 'Instrukcje: Implementowanie Znajdź i Zamień mechanizm | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3847b9125109cd48b458d06cbfc41fa91b7139f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943028"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>Instrukcje: Implementowanie Znajdź i Zamień mechanizm

Program Visual Studio udostępnia dwa sposoby wdrażania Znajdź/Zamień. Jednym ze sposobów jest przekazać obraz tekstu do powłoki i pozwól mu obsługę wyszukiwania, wyróżniania i zastępowanie tekstu. Dzięki temu użytkownicy mogą określić wiele zakresów tekstu. Alternatywnie Twoje pakietu VSPackage można kontrolować ta sama funkcja. W obu przypadkach należy powiadomić powłoki o bieżący element docelowy i elementy docelowe wszystkie otwarte dokumenty.

## <a name="to-implement-findreplace"></a>Aby zaimplementować Znajdź i Zamień

1. Implementowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> interfejsu na jednym z obiektów zwróconych przez właściwości ramki <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView> lub <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>. Jeśli tworzysz niestandardowy edytor, powinien implementować ten interfejs jako część klasy edytora niestandardowego.

2. Użyj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> metody, aby określić opcje, które obsługuje edytora i, aby wskazać, czy implementuje wyszukiwanie obrazów tekstu.

   Jeśli Edytor obsługuje wyszukiwanie obrazów tekstu, należy zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>.

   W przeciwnym razie zaimplementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>.

3. W przypadku zaimplementowania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> metody, można ułatwić wyszukiwanie zadań, wywołując <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> interfejsu.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>