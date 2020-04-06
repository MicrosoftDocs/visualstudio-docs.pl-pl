---
title: Dostarczanie wsparcia cofania projektantom | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], undo support
ms.assetid: 43eb1f14-b129-404a-8806-5bf9b099b67b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0580f974c362a71c3e400946f2ad34f565ad1232
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699676"
---
# <a name="supply-undo-support-to-designers"></a>Dostarczanie wsparcia cofania dla projektantów

Projektanci, takich jak edytory, zazwyczaj trzeba obsługiwać operacje cofania, dzięki czemu użytkownicy mogą odwrócić ich ostatnich zmian podczas modyfikowania elementu kodu.

Większość projektantów zaimplementowanych w programie Visual Studio ma "cofnij" wsparcie automatycznie dostarczone przez środowisko.

Implementacje projektanta, które muszą zapewnić obsługę funkcji cofania:

- Zapewnij zarządzanie cofania, implementując abstrakcyjną klasę podstawową<xref:System.ComponentModel.Design.UndoEngine>

- Trwałość dostaw i codedom wsparcia <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> przez implementowanie i klas.

Aby uzyskać więcej informacji na temat pisania projektantów przy użyciu programu .NET Framework, zobacz [Rozszerzanie pomocy technicznej w czasie projektowania](/previous-versions/37899azc(v=vs.140)).

Zapewnia [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] domyślną infrastrukturę cofania przez:

- Dostarczanie implementacji zarządzania <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> cofania za pośrednictwem i <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> klas.

- Dostarczanie trwałości i codedom wsparcia <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> <xref:System.ComponentModel.Design.IComponentChangeService> za pośrednictwem domyślnych i implementacji.

## <a name="obtain-undo-support-automatically"></a>Automatyczne uzyskiwanie pomocy technicznej cofania

Każdy projektant utworzony w programie Visual Studio ma automatyczną i pełną obsługę cofania, jeśli projektant:

- Korzysta z <xref:System.Windows.Forms.Control> klasy opartej dla interfejsu użytkownika.

- Wykorzystuje standardowy system generowania i analizowania kodu opartego na kodzie dla generowania i trwałości kodu.

   Aby uzyskać więcej informacji na temat pracy z pomocą techniczną programu Visual Studio CodeDOM, zobacz [Generowanie i kompilacja dynamicznego kodu źródłowego.](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation)

## <a name="when-to-use-explicit-designer-undo-support"></a>Kiedy używać jawnej obsługi cofania projektanta
 Projektanci muszą podać własne zarządzanie cofaniem, jeśli używają graficznego interfejsu użytkownika, określanego jako <xref:System.Windows.Forms.Control>karta widoku, innej niż dostarczona przez program .

 Przykładem tego może być utworzenie produktu z interfejsem graficznym opartym na sieci Web, a nie interfejsem graficznym opartym na platformie .NET Framework.

 W takich przypadkach należy zarejestrować tę kartę widoku <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute>w programie Visual Studio przy użyciu programu Visual Studio i zapewnić jawne zarządzanie cofania.

 Projektanci muszą zapewnić obsługę CodeDOM i trwałości, jeśli nie używają modelu <xref:System.CodeDom> generowania kodu programu Visual Studio dostępnego w przestrzeni nazw.

## <a name="undo-support-features-of-the-designer"></a>Cofanie funkcji pomocy technicznej projektanta
 Środowisko SDK zawiera domyślne implementacje interfejsów potrzebnych do zapewnienia obsługi <xref:System.Windows.Forms.Control> cofania, które mogą być używane przez projektantów nie używających klas opartych na ich interfejsach użytkownika lub standardowego modelu CodeDOM i trwałości.

 Klasa <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> pochodzi z klasy .NET Framework <xref:System.ComponentModel.Design.UndoEngine> przy <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> użyciu implementacji klasy do zarządzania operacjami cofania.

 Visual Studio udostępnia następującą funkcję do projektanta cofnąć:

- Połączone funkcje cofania w wielu projektantach.

- Jednostki podrzędne w projektancie mogą <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> wchodzić w interakcje z rodzicami, implementując i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> włączając <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>.

Środowisko SDK zapewnia CodeDOM i trwałości wsparcia przez dostarczanie:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService>jako wdrożenie<xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- Dostarczone <xref:System.ComponentModel.Design.IComponentChangeService> przez hosta projektu programu Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Korzystanie z funkcji SDK środowiska do dostarczania pomocy technicznej cofania

Aby uzyskać obsługę cofania, obiekt implementujący projektanta musi utworzyć <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> wystąpienie i <xref:System.IServiceProvider> zainicjować wystąpienie klasy z prawidłową implementacją. Ta <xref:System.IServiceProvider> klasa musi zapewnić następujące usługi:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Projektanci korzystający z serializacji CodeDOM <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> programu [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Visual Studio mogą <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>wybrać użycie dostarczonego z jego implementacją .

   W takim przypadku <xref:System.IServiceProvider> klasa podana do konstruktora <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> należy <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> zwrócić ten obiekt jako implementację klasy.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Projektanci używający <xref:System.ComponentModel.Design.DesignSurface> wartości domyślnej dostarczonej przez hosta projektu <xref:System.ComponentModel.Design.IComponentChangeService> programu Visual Studio mają gwarancję domyślnej implementacji klasy.

Projektanci implementujący <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> oparty mechanizm cofania automatycznie śledzi zmiany, jeśli:

- Zmiany właściwości są <xref:System.ComponentModel.TypeDescriptor> wprowadzane za pośrednictwem obiektu.

- <xref:System.ComponentModel.Design.IComponentChangeService>zdarzenia są generowane ręcznie, gdy zostanie zatwierdzona cofnięta zmiana.

- Modyfikacja projektanta została utworzona w <xref:System.ComponentModel.Design.DesignerTransaction>kontekście .

- Projektant decyduje się jawnie utworzyć cofanie jednostek przy użyciu standardowej <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> jednostki cofania dostarczonej przez implementację lub <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit>implementację specyficzną dla programu Visual Studio, która wywodzi się z <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> i zapewnia również implementację obu <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit>.

## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Rozszerz obsługę czasu projektowania](/previous-versions/37899azc(v=vs.140))
