---
title: Dostarczanie obsługi Cofnij do projektantów | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80699676"
---
# <a name="supply-undo-support-to-designers"></a>Dostarcz obsługę cofania dla projektantów

Projektanci, podobnie jak edytory, zazwyczaj muszą obsługiwać operacje cofania, dzięki czemu użytkownicy mogą odwracać ostatnie zmiany podczas modyfikacji elementu kodu.

Większość projektantów wdrożonych w programie Visual Studio ma pomoc techniczną "undo" automatycznie dostarczoną przez środowisko.

Implementacje projektanta, które muszą zapewnić obsługę funkcji cofania:

- Zapewnij zarządzanie Cofnij przez implementację abstrakcyjnej klasy podstawowej <xref:System.ComponentModel.Design.UndoEngine>

- Zapewnij obsługę trwałości i CodeDOM, implementując <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>  <xref:System.ComponentModel.Design.IComponentChangeService> klasy i.

Aby uzyskać więcej informacji na temat pisania projektantów przy użyciu .NET Framework, zobacz temat [zwiększanie obsługi czasu projektowania](/previous-versions/37899azc(v=vs.140)).

Program [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] udostępnia domyślną infrastrukturę cofania według:

- Udostępnianie implementacji cofania zarządzania za <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> pomocą <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> klas i.

- Zapewnianie obsługi trwałości i CodeDOM przy użyciu domyślnych <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> i <xref:System.ComponentModel.Design.IComponentChangeService> implementacji.

## <a name="obtain-undo-support-automatically"></a>Automatyczne uzyskiwanie pomocy technicznej

Każdy projektant utworzony w programie Visual Studio ma automatyczne i pełne wsparcie cofania, jeśli projektant:

- Używa <xref:System.Windows.Forms.Control> klasy bazującej na interfejsie użytkownika.

- Wykorzystuje standardowy system generowania kodu oparty na CodeDOM i umożliwiający generowanie kodu i trwałość.

   Aby uzyskać więcej informacji na temat pracy z obsługą języka CodeDOM programu Visual Studio, zobacz [dynamiczne generowanie kodu źródłowego i kompilacja](/dotnet/framework/reflection-and-codedom/dynamic-source-code-generation-and-compilation).

## <a name="when-to-use-explicit-designer-undo-support"></a>Kiedy używać jawnego projektanta Cofnij obsługę
 Projektanci muszą podać własne zarządzanie cofaniem, jeśli korzystają z graficznego interfejsu użytkownika, nazywanego adapterem widoku, innym niż dostarczony przez <xref:System.Windows.Forms.Control> .

 Przykładem może być tworzenie produktu przy użyciu graficznego interfejsu projektowego opartego na sieci Web, a nie interfejsu graficznego opartego na .NET Framework.

 W takich przypadkach należy zarejestrować ten adapter widoku w programie Visual Studio przy użyciu <xref:Microsoft.VisualStudio.Shell.Design.ProvideViewAdapterAttribute> i zapewnić jawne zarządzanie Cofnij.

 Projektanci muszą zapewnić obsługę CodeDOM i trwałości, jeśli nie korzystają z modelu generowania kodu programu Visual Studio dostarczonego w <xref:System.CodeDom> przestrzeni nazw.

## <a name="undo-support-features-of-the-designer"></a>Cofnij funkcje obsługi projektanta
 Zestaw SDK środowiska udostępnia domyślne implementacje interfejsów, które są konieczne w celu zapewnienia obsługi Cofnij, które mogą być używane przez projektantów nie korzystających z <xref:System.Windows.Forms.Control> klas opartych na interfejsach użytkownika lub standardowych modeli CodeDOM i trwałości.

 <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>Klasa pochodzi z <xref:System.ComponentModel.Design.UndoEngine> klasy .NET Framework przy użyciu implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoManager> klasy do zarządzania operacjami cofania.

 Program Visual Studio udostępnia następującą funkcję do cofnięcia projektanta:

- Połączone funkcje cofania w wielu projektantach.

- Jednostki podrzędne w projektancie mogą korzystać z obiektów nadrzędnych przez implementację <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> włączony <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> .

Zestaw SDK środowiska zapewnia obsługę CodeDOM i trwałości, dostarczając:

- <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> jako implementacja <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

- <xref:System.ComponentModel.Design.IComponentChangeService>Dostarczone przez hosta projektu programu Visual Studio.

## <a name="use-the-environment-sdk-features-to-supply-undo-support"></a>Korzystanie z funkcji zestawu SDK środowiska w celu zapewnienia pomocy technicznej Undo

Aby uzyskać pomoc techniczną, obiekt implementujący projektanta musi tworzyć wystąpienia i inicjować wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> klasy z prawidłową <xref:System.IServiceProvider> implementacją. Ta <xref:System.IServiceProvider> Klasa musi zapewniać następujące usługi:

- <xref:System.ComponentModel.Design.IDesignerHost>.

- <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService>

   Projektanci korzystający z serializacji CodeDOM programu Visual Studio mogą wybrać użycie <xref:System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService> z użyciem [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] jako implementacji <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> .

   W takim przypadku <xref:System.IServiceProvider> Klasa udostępniona <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> konstruktorowi powinna zwrócić ten obiekt jako implementację <xref:System.ComponentModel.Design.Serialization.IDesignerSerializationService> klasy.

- <xref:System.ComponentModel.Design.IComponentChangeService>

   Projektanci korzystający z wartości domyślnej <xref:System.ComponentModel.Design.DesignSurface> dostarczonej przez hosta projektu programu Visual Studio mają zagwarantowaną domyślną implementację <xref:System.ComponentModel.Design.IComponentChangeService> klasy.

Projektanci implementujący <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine> mechanizm cofania automatycznie śledzą zmiany, jeśli:

- Zmiany właściwości są wprowadzane za pomocą <xref:System.ComponentModel.TypeDescriptor> obiektu.

- <xref:System.ComponentModel.Design.IComponentChangeService> zdarzenia są generowane ręcznie po zatwierdzeniu zmiany do cofnięcia.

- Modyfikacja projektanta została utworzona w kontekście <xref:System.ComponentModel.Design.DesignerTransaction> .

- Projektant pozwala jawnie utworzyć jednostki cofania przy użyciu standardowej jednostki cofania dostarczonej przez implementację <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> lub implementację specyficzną dla programu Visual Studio <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine.UndoUnit> , która pochodzi od <xref:System.ComponentModel.Design.UndoEngine.UndoUnit> i zawiera również implementację obu <xref:Microsoft.VisualStudio.OLE.Interop.IOleUndoUnit> i <xref:Microsoft.VisualStudio.OLE.Interop.IOleParentUndoUnit> .

## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.Design.UndoEngine>
- <xref:Microsoft.VisualStudio.Shell.Design.OleUndoEngine>
- [Zwiększ obsługę czasu projektowania](/previous-versions/37899azc(v=vs.140))
