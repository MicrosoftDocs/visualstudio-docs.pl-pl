---
title: Inicjalizacja projektanta i konfiguracja metadanych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e876dd9e6fa95bbe180d1737bc8c4911f16e1e9a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712214"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicjowanie projektanta i konfiguracja metadanych

Manipulowanie metadanych i atrybutów filtru skojarzonych z projektantem lub składnikiem projektanta zapewnia mechanizm <xref:System.Type> dla aplikacji do definiowania, które narzędzia są używane przez określonego projektanta do obsługi różnych obiektów (takich jak struktury danych, klasy lub jednostek graficznych), gdy projektant jest dostępny i jak Visual Studio IDE jest skonfigurowany do obsługi projektanta (na przykład, które **kategorii przybornika** lub karty jest dostępna).

Zapewnia [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] kilka mechanizmów ułatwiających kontrolę inicjowania projektanta lub projektanta składnika i manipulowania jego metadanych przez VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Inicjowanie metadanych i informacji o konfiguracji
 Ponieważ są one ładowane na żądanie, vsPackages może nie zostały załadowane przez środowisko programu Visual Studio przed wystąpienie projektanta. W związku z tym VSPackages nie można użyć standardowego mechanizmu do konfigurowania projektanta lub projektanta składnika podczas tworzenia, który jest do obsługi <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> zdarzenia. Zamiast tego VSPackage implementuje wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> interfejsu i rejestruje się w celu zapewnienia dostosowań, określane jako rozszerzenia powierzchni projektu.

### <a name="customize-initialization"></a>Dostosowywanie inicjowania

Dostosowywanie projektanta, składnika lub powierzchni projektanta obejmuje:

1. Modyfikowanie metadanych projektanta i <xref:System.Type> skutecznie zmieniając sposób, w jaki niektóre są dostępne lub konwertowane.

    Zazwyczaj odbywa się to <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> za pośrednictwem mechanizmów lub.

    Na przykład <xref:System.Windows.Forms>podczas inicjowania projektantów opartych <xref:System.Drawing.Design.UITypeEditor> na <xref:System.Web.UI.WebControls.Image> programie Visual Studio środowisko programu Visual Studio modyfikuje dla obiektów używanych z projektantem, aby użyć Menedżera zasobów do uzyskania map bitowych, a nie systemu plików.

2. Integracja ze środowiskiem, na przykład przez subskrybowanie zdarzeń lub uzyskiwanie informacji o konfiguracji projektu. Można uzyskać informacje o konfiguracji projektu i subskrybować zdarzenia, uzyskując <xref:System.ComponentModel.Design.ITypeResolutionService> interfejs.

3. Modyfikacja środowiska użytkownika przez aktywację odpowiednich kategorii **przybornika** lub ograniczając zastosowanie projektanta przez <xref:System.ComponentModel.ToolboxItemFilterAttribute> zastosowanie wystąpienia klasy do projektanta.

### <a name="designer-initialization-by-a-vspackage"></a>Inicjowanie projektanta przez pakiet VSPackage

VsPackage powinien obsługiwać inicjalizacji projektanta przez:

1. Tworzenie obiektu implementującego <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> klasę.

   > [!NOTE]
   > Klasa <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> nigdy nie powinny być implementowane <xref:Microsoft.VisualStudio.Shell.Package> na tym samym obiekcie jako klasy.

2. Rejestrowanie klasy, która <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> implementuje jako zapewnienie obsługi rozszerzeń projektanta VSPackage. Zarejestruj klasę, stosując wystąpienia <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>i <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do klasy, która zapewnia implementację <xref:Microsoft.VisualStudio.Shell.Package>VSPackage .

Za każdym razem, gdy tworzony jest składnik projektanta lub projektanta, środowisko programu Visual Studio:

- Uzyskuje dostęp do każdego zarejestrowanego dostawcy rozszerzenia powierzchni projektu.

- Wystąpienia i inicjuje wystąpienie każdego <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiektu dostawcy rozszerzenia powierzchni projektu.

- Wywołuje metodę lub <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> metodę każdego dostawcy rozszerzenia powierzchni projektowej (stosownie do przypadku).

Podczas implementowania <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiektu jako elementu członkowskiego VSPackage, ważne jest, aby zrozumieć, że:

- Środowisko programu Visual Studio nie zapewnia żadnej kontroli nad metadanymi lub innymi ustawieniami konfiguracji modyfikowanych przez określonego `DesignSurfaceExtension` dostawcę. Jest możliwe dla dwóch `DesignSurfaceExtension` lub więcej dostawców modyfikujących tę samą funkcję projektanta w sposób powodujący konflikt, przy czym ostateczna modyfikacja jest ostateczna. Jest nieokreślony, która modyfikacja jest ostatnio stosowana.

- Jest możliwe jawnie ograniczyć implementację <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiektu do określonych projektantów, <xref:System.ComponentModel.ToolboxItemFilterAttribute> stosując wystąpienia do tej implementacji. Aby uzyskać więcej informacji na temat <xref:System.ComponentModel.ToolboxItemFilterAttribute> filtrowania elementów **przybornika,** zobacz i <xref:System.ComponentModel.ToolboxItemFilterType>.

## <a name="additional-metadata-provisioning"></a>Dodatkowe inicjowanie obsługi administracyjnej metadanych

VsPackage można zmienić konfigurację projektanta lub składnika projektanta innych niż w czasie projektowania.

Klasa <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> może być używana programowo lub stosowane do VSPackage, który zapewnia projektanta.

Wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> klasy służy do modyfikowania metadanych składników utworzonych na powierzchni projektowej. Na przykład można zastąpić domyślną przeglądarkę właściwości używaną przez <xref:System.Windows.Forms.CommonDialog> obiekty przeglądarką właściwości niestandardowych.

Modyfikacje dostarczone przez <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> wystąpienie zastosowane do implementacji VSPackage <xref:Microsoft.VisualStudio.Shell.Package> może mieć jeden z dwóch zakresów:

- Global -- dla wszystkich nowych wystąpień danego składnika

- Lokalny — odnoszący się tylko do wystąpienia składnika utworzonego na powierzchni projektowej dostarczonej przez bieżący vspackage.

Właściwość `IsGlobal` <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> wystąpienia stosowane do vspackage implementacji <xref:Microsoft.VisualStudio.Shell.Package> określa ten zakres.

Zastosowanie atrybutu do implementacji <xref:Microsoft.VisualStudio.Shell.Package> z <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> właściwością <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> obiektu `true`ustawionego na , jak poniżej, zmienia przeglądarkę dla całego środowiska programu Visual Studio:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Jeśli flaga globalna `false`została ustawiona na , a następnie zmiana metadanych jest lokalny dla bieżącego projektanta obsługiwane przez bieżącego VSPackage:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> Powierzchnia projektowa obsługuje tylko tworzenie składników i dlatego tylko składniki mogą mieć lokalne metadane. W powyższym przykładzie próbowano zmodyfikować właściwość, taką `Color` jak właściwość obiektu. Jeśli `false` został przekazany do flagi `CustomBrowser` globalnej, nigdy nie pojawi się, ponieważ projektant nigdy nie tworzy wystąpienia `Color`. Ustawienie flagi globalnej `false` jest przydatne w przypadku składników, takich jak formanty, czasomierze i okna dialogowe.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Rozszerzenie wsparcia w czasie projektowania](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
