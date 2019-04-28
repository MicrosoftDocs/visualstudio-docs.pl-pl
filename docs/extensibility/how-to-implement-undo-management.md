---
title: 'Instrukcje: Implementowanie zarządzania cofania | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - undo management
ms.assetid: 1942245d-7a1d-4a11-b5e7-a3fe29f11c0b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b29b95b9c53f18d6f97ac2455dd30aa6e26ccde4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63415478"
---
# <a name="how-to-implement-undo-management"></a>Instrukcje: Implementowanie cofania zarządzania
Podstawowy interfejs używany do zarządzania cofania jest <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>, który jest implementowany przez środowisko. Do obsługi zarządzania cofania, implementować jednostek cofania oddzielne (oznacza to, <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit>, która może zawierać wiele poszczególne kroki.

 Sposób implementacji zarządzania cofania różni się zależnie od tego, czy edytor obsługuje wiele widoków, czy nie. Procedury dla każdego wdrożenia są szczegółowo opisane w poniższych sekcjach.

## <a name="cases-where-an-editor-supports-a-single-view"></a>Przypadków, gdy Edytor obsługuje pojedynczy widok
 W tym scenariuszu edytor nie obsługuje wielu widoków. Istnieje tylko jeden z nich i jeden dokument, a ich obsługuje operacji cofania. Poniższa procedura umożliwia Implementowanie zarządzania cofania.

### <a name="to-support-undo-management-for-a-single-view-editor"></a>Do obsługi zarządzania cofania dla edytora pojedynczego widoku

1. Wywołaj `QueryInterface` na `IServiceProvider` interfejsu na ramki okna dla `IOleUndoManager`, z obiektu widoku dokumentu do dostępu do menedżera cofania (`IID_IOLEUndoManager`).

2. Gdy widok jest ulokowany do ramki okna, otrzymuje wskaźnik witryny, której można użyć do wywołania `QueryInterface` dla `IServiceProvider`.

## <a name="cases-where-an-editor-supports-multiple-views"></a>Przypadków, gdy Edytor obsługuje wiele widoków
 Jeśli masz separacji dokument i widok, występuje menedżera cofania zwykle co skojarzone z dokumentem. Wszystkie jednostki cofania są umieszczane w menedżera cofania co skojarzony z obiektem danych dokumentu.

 Zamiast wyświetlanie, wykonywanie zapytań dotyczących menedżera cofania, w których jest on dostępny dla każdego widoku, dane dokumentu obiekt wywołania <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> do utworzenia wystąpienia menedżera cofania, określając identyfikator klasy CLSID_OLEUndoManager. Identyfikator klasy jest zdefiniowany w *OCUNDOID.h* pliku.

 Korzystając z <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> do utworzenia własnego wystąpienia menedżera cofania, należy użyć poniższej procedury można dołączyć Menedżera cofania do środowiska.

### <a name="to-hook-your-undo-manager-into-the-environment"></a>Można dołączyć Menedżera cofania do środowiska

1. Wywołaj `QueryInterface` na obiekt zwrócony z <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> dla `IID_IOleUndoManager`. Wskaźnik do Store <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager>.

2. Wywołaj `QueryInterface` na `IOleUndoManager` dla `IID_IOleCommandTarget`. Wskaźnik do Store <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

3. Przekaźnik usługi <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> wywołania do przechowywanej `IOleCommandTarget` interfejsu dla następujących poleceń StandardCommandSet97:

   - cmdidUndo

   - cmdidMultiLevelUndo

   - cmdidRedo

   - cmdidMultiLevelRedo

   - cmdidMultiLevelUndoList

   - cmdidMultiLevelRedoList

4. Wywołaj `QueryInterface` na `IOleUndoManager` dla `IID_IVsChangeTrackingUndoManager`. Wskaźnik do Store <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>.

    Za pomocą wskaźnika do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager> do wywołania <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.MarkCleanState%2A>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.AdviseTrackingClient%2A>i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager.UnadviseTrackingClient%2A> metody.

5. Wywołaj `QueryInterface` na `IOleUndoManager` dla `IID_IVsLinkCapableUndoManager`.

6. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkCapableUndoManager.AdviseLinkedUndoClient%2A> z dokumentu, które powinny również implementować <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoClient> interfejsu. Po zamknięciu dokumentu wywołania `IVsLinkCapableUndoManager::UnadviseLinkedUndoClient`.

7. Po zamknięciu dokumentu wywołać `QueryInterface` na Twojego menedżera cofania `IID_IVsLifetimeControlledObject`.

8. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject.SeverReferencesToOwner%2A>.

9. Gdy zmiany zostaną wprowadzone do dokumentu, należy wywołać <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> w Menedżerze z `OleUndoUnit` klasy. <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A> Metoda przechowuje odwołania do obiektu, więc zazwyczaj, zwolnij go zaraz po <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager.Add%2A>.

   `OleUndoManager` Klasa reprezentuje wystąpienie stosu pojedynczą czynność cofnięcia. W efekcie jest jeden obiekt menedżera cofania na jednostkę danych są śledzone dla cofania i ponawiania.

> [!NOTE]
> Gdy obiekt menedżera cofania jest często używany przez Edytor tekstu, jest ogólnego składnika, który nie obsługuje określonego edytora tekstu. Chcąc obsługuje wielopoziomowe cofnięcie ani ponownego wykonywania, można użyć tego obiektu, aby to zrobić.

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsChangeTrackingUndoManager>
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLifetimeControlledObject>
- [Instrukcje: Wyczyścić stosu cofania](../extensibility/how-to-clear-the-undo-stack.md)