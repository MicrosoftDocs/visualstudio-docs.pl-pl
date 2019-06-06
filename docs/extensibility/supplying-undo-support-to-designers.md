---
title: Dostarczanie Cofnij pomocy technicznej do projektantów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e243ccfc92c5e17dd25e6d77dede439daac08761
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747726"
---
# <a name="supply-undo-support-to-designers"></a>Podaj Obsługa polecenia Cofnij do projektantów

Projektanci, takie jak edytory, zazwyczaj należy do obsługi operacji cofania, dzięki czemu użytkownicy można cofnąć ich ostatnich zmian podczas modyfikowania elementu kodu.

Większość projektantów zaimplementowane w Visual Studio mają "Cofnij" Pomoc techniczna jest świadczona w automatycznie przez środowisko.

Projektanta implementacji, które są potrzebne, aby zapewnić obsługę funkcji cofania:

- Zapewnia zarządzania cofania poprzez implementację abstrakcyjnej klasy bazowej <xref:System.ComponentModel.Design.UndoEngine>

- Trwałość dostarczają i CodeDOM obsługuje implementując <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> i <xref:System.ComponentModel.Design.IComponentChangeService> klasy.

Aby uzyskać więcej informacji o pisaniu projektantów przy użyciu .NET Framework, zobacz [rozszerzenie obsługi w czasie projektowania](/previous-versions/37899azc(v=vs.140)).

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Zapewnia infrastrukturę cofania domyślne przez:

- Zapewnianie Cofnij implementacji zarządzania za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> i <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> klasy.

- Dostarczanie trwałości oraz obsługi modelu CodeDOM za pomocą domyślnego <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> i <xref:System.ComponentModel.Design.IComponentChangeService> implementacji.

## <a name="obtain-undo-support-automatically"></a>Uzyskaj Obsługa polecenia Cofnij automatycznie

Projektanta w programie Visual Studio obsługuje automatyczne i pełne cofania if, Projektant:

- Sprawia, że użycie <xref:System.Windows.Forms.Control> na podstawie klasy interfejs użytkownika.

- Stosuje systemu podczas analizowania i generowanie kodu na podstawie CodeDOM standardowego dla generowania kodu i trwałości.

   Aby uzyskać więcej informacji na temat pracy z obsługą programu Visual Studio CodeDOM, zobacz [dynamiczne generowanie kodu źródłowego i kompilacja](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Kiedy należy używać jawnych cofania projektanta pomocy technicznej
 Projektanci należy podać zarządu cofania, jeśli korzystają z graficznym interfejsem użytkownika, określane jako karty Widok innej niż ta, dostarczone przez <xref:System.Windows.Forms.Control>.

 Na przykład może być tworzenia produktu z interfejsem sieci web projektu graficznego, a nie interfejsu graficznego środowiska .NET Framework.

 W takich przypadkach jeden konieczne zarejestrowanie programu Visual Studio przy użyciu tej karty Widok <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>i zarządzanie jawne cofania.

 Projektanci konieczne jest zapewnienie CodeDOM i trwałość obsługuje, jeśli nie należy używać modelu generowania kodu programu Visual Studio w <xref:System.CodeDom> przestrzeń nazw.

## <a name="undo-support-features-of-the-designer"></a>Cofnij obsługują funkcje projektanta
 Zestaw SDK środowiska zawiera implementacje domyślne klasy interfejsy niezbędne do zapewnienia Cofnij pomocy technicznej, które mogą być używane przez projektantów nie używa <xref:System.Windows.Forms.Control> na podstawie klasy dla ich interfejsów użytkownika lub standardowego modelu CodeDOM i trwałości.

 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> Klasa pochodzi od programu .NET Framework <xref:System.ComponentModel.Design.UndoEngine> przy użyciu implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> klasy, aby zarządzać cofania operacji.

 Program Visual Studio zawiera następującą funkcję do projektanta cofania:

- Funkcje połączonego cofania w wielu projektantów.

- Jednostki podrzędne w Projektancie mogą wchodzić w interakcje z nadrzędnych implementując <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> na <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.

Zestaw SDK środowiska umożliwia obsługę CodeDOM i trwałości poprzez dostarczenie:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> jako implementacja <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- A <xref:System.ComponentModel.Design.IComponentChangeService> udostępniane przez hosta projektu programu Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Użyj funkcji zestawu SDK środowiska, aby określić Obsługa polecenia Cofnij

Aby uzyskać Obsługa polecenia Cofnij, obiekt Implementowanie projektanta musi tworzyć wystąpienie i inicjuje wystąpienie klasy <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> klasy przy użyciu prawidłowego <xref:System.IServiceProvider> implementacji. To <xref:System.IServiceProvider> klasy należy podać następujące usługi:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Projektanci przy użyciu programu Visual Studio CodeDOM serializacji może wybrać <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> dołączonym [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] jako jego implementacja obiektu <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>.

   W tym przypadku <xref:System.IServiceProvider> klasy udostępniane <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> konstruktora powinna zwrócić implementację tego obiektu <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> klasy.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Projektanci przy użyciu domyślnego <xref:System.ComponentModel.Design.DesignSurface> dostarczone przez projekt programu Visual Studio hosta musi mieć domyślną implementację elementu <xref:System.ComponentModel.Design.IComponentChangeService> klasy.

Implementowanie projektantów <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> cofania na podstawie mechanizmu automatycznie śledzi zmiany, jeśli:

- Zmiany właściwości są nawiązywane przy użyciu <xref:System.ComponentModel.TypeDescriptor> obiektu.

- <xref:System.ComponentModel.Design.IComponentChangeService> zdarzenia są generowane ręcznie, gdy można cofnąć zmiana zostaje zatwierdzona.

- Modyfikowanie w Projektancie został utworzony w kontekście <xref:System.ComponentModel.Design.DesignerTransaction>.

- Projektant postanowi jawnie jednostek cofania przy użyciu jednej jednostki standardowe cofania, dostarczone przez implementację <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> lub implementacji programu Visual Studio specyficzne dla <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>, które wywodzi się z <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> a także Implementacja obu <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.

## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Rozszerzenie obsługi w czasie projektowania](/previous-versions/37899azc(v=vs.140))