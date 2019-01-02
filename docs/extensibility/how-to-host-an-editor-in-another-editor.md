---
title: 'Instrukcje: Hostowanie redaktorem w innym edytorze | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a9de111a1747e9f5451bff2c8bd3e5edf171d9a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833610"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Instrukcje: Host redaktorem w innym edytorze

W programie Visual Studio umożliwia hostowanie jednym edytorze wewnątrz innego, określając okna hostowania jako okno nadrzędne. Aby to zrobić, należy ustawić parametry <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> i <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> na ramki okna podrzędnego.

## <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Aby ustawić ramki okna obsługi edytora

1.  Wyznaczanie redaktorem hostowanej edytora, tworząc okienko okna podrzędnego.

     To okienko jest, gdzie edytora tekstu.

2.  Utwórz Edytor hostingu za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> metody.

3.  Ustaw <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> i <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> właściwości w celu wykonania ramki okna edytora hostowanej przez przekazanie te właściwości jako parametry w celu <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> metody, odpowiednio.

     Jeśli musisz pobrać te parametry, należy przekazać te właściwości, aby <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metody.

4.  Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metoda zawartej edytora.

     Edytor zostanie wyświetlony w okienku hostowanej zawierającego edytora.

## <a name="robust-programming"></a>Skuteczne programowanie

**Projektanta aplikacji** w Visual Studio Team Edition dla architektów jest przykładem ramki okna edytora obsługującego innym edytorze. **Projektanta aplikacji** hostuje innych projektantów w jej okienku po prawej stronie. Panel projektanta (lub **właściwości** stronie) dla każdej zawartej projektantów jest dodawany do zawierającego ramki okna.