---
title: Inicjowanie projektanta i konfiguracja metadanych | Microsoft Docs
description: Dowiedz się, w jaki sposób zestaw SDK programu Visual Studio ułatwia kontrolowanie inicjalizacji i metadanych składnika projektanta oraz jego metadane przez pakietu VSPackage.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9907298cf730d6e51c108dc92f633d0b50451f12
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996165"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicjowanie projektanta i konfiguracja metadanych

Manipulowanie metadanymi i atrybutami filtrów skojarzonymi z projektantem lub składnikiem projektanta zapewnia mechanizm do definiowania, które narzędzia są używane przez określony Projektant do obsługi różnych <xref:System.Type> obiektów (takich jak struktury danych, klasy lub jednostki graficzne), gdy Projektant jest dostępny, a także sposób, w jaki środowisko IDE programu Visual Studio jest skonfigurowane do obsługi projektanta (na przykład  dostępność kategorii lub karty).

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]Zapewnia kilka mechanizmów ułatwiających kontrolę inicjalizacji składnika projektanta lub projektanta oraz manipulowanie jego metadanymi przez pakietu VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Zainicjuj informacje o metadanych i konfiguracji
 Ponieważ są one ładowane na żądanie, pakietów VSPackage mogły nie zostać załadowane przez środowisko programu Visual Studio przed wystąpieniem projektanta. W związku z tym pakietów VSPackage nie może używać standardowego mechanizmu do konfigurowania projektanta lub składnika projektanta podczas tworzenia, który ma obsłużyć <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> zdarzenie. Zamiast tego pakietu VSPackage implementuje wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> interfejsu i rejestruje się w celu zapewnienia dostosowań, nazywanych rozszerzeniami powierzchni projektowania.

### <a name="customize-initialization"></a>Dostosuj inicjalizację

Dostosowywanie projektanta, składnika lub powierzchni projektanta obejmuje:

1. Modyfikowanie metadanych projektanta i efektywne Zmienianie sposobu <xref:System.Type> uzyskiwania dostępu do określonego lub konwersji.

    Zwykle jest to realizowane za pomocą <xref:System.Drawing.Design.UITypeEditor> <xref:System.ComponentModel.TypeConverter> mechanizmów lub.

    Na przykład po <xref:System.Windows.Forms> zainicjowaniu projektantów opartych na czasie program Visual Studio modyfikuje <xref:System.Drawing.Design.UITypeEditor> <xref:System.Web.UI.WebControls.Image> obiekty używane z projektantem, aby użyć Menedżera zasobów do uzyskiwania map bitowych zamiast systemu plików.

2. Integracja ze środowiskiem, na przykład przez subskrybowanie zdarzeń lub uzyskiwanie informacji o konfiguracji projektu. Możesz uzyskać informacje o konfiguracji projektu i subskrybować zdarzenia, uzyskując <xref:System.ComponentModel.Design.ITypeResolutionService> interfejs.

3. Modyfikacja środowiska użytkownika przez aktywowanie odpowiednich kategorii **przybornika** lub ograniczenie możliwości projektowania przez zastosowanie instancji <xref:System.ComponentModel.ToolboxItemFilterAttribute> klasy do projektanta.

### <a name="designer-initialization-by-a-vspackage"></a>Inicjowanie projektanta przez pakietu VSPackage

Pakietu VSPackage powinien obsługiwać inicjalizację projektanta przez:

1. Tworzenie obiektu implementującego <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> klasę.

   > [!NOTE]
   > <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>Klasy nigdy nie należy implementować na tym samym obiekcie co <xref:Microsoft.VisualStudio.Shell.Package> Klasa.

2. Rejestrowanie klasy implementującej <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obsługę rozszerzeń projektanta pakietu VSPackage. Zarejestruj klasę, stosując wystąpienia  <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute> , <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> i <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do klasy, która dostarcza implementację pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> .

Za każdym razem, gdy tworzony jest składnik Projektant lub Projektant, środowisko programu Visual Studio:

- Uzyskuje dostęp do każdego zarejestrowanego dostawcy rozszerzeń powierzchni projektowej.

- Tworzy wystąpienia i Inicjuje wystąpienie każdego obiektu dostawcy rozszerzenia powierzchni projektowej <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> .

- Wywołuje każdą metodę lub metodę dostawcy rozszerzenia powierzchni projektowej <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> (zgodnie z potrzebami).

Podczas implementowania <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiektu jako elementu członkowskiego pakietu VSPackage należy zrozumieć, że:

- Środowisko programu Visual Studio nie zapewnia żadnej kontroli nad tym, jakie metadane lub inne ustawienia konfiguracji `DesignSurfaceExtension` są modyfikowane przez określonego dostawcę. Istnieje możliwość, że co najmniej dwóch `DesignSurfaceExtension` dostawców modyfikuje tę samą funkcję projektanta w sprzecznych sposobach wraz z ostateczną modyfikacją. Nie jest to nieokreślone, która modyfikacja została ostatnio zastosowana.

- Można jawnie ograniczyć implementację <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiektu do określonych projektantów, stosując wystąpienia <xref:System.ComponentModel.ToolboxItemFilterAttribute> dla tej implementacji. Aby uzyskać więcej informacji na temat filtrowania elementów **przybornika** , zobacz <xref:System.ComponentModel.ToolboxItemFilterAttribute> i <xref:System.ComponentModel.ToolboxItemFilterType> .

## <a name="additional-metadata-provisioning"></a>Dodatkowe Inicjowanie obsługi metadanych

Pakietu VSPackage może zmienić konfigurację projektanta lub składnika projektanta innego niż w czasie projektowania.

<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute>Klasa może być używana programowo lub zastosowana do pakietu VSPackage, która udostępnia projektanta.

Wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> klasy służy do modyfikowania metadanych składników utworzonych na powierzchni projektowej. Na przykład jedna może zastąpić domyślną przeglądarkę właściwości używaną przez <xref:System.Windows.Forms.CommonDialog> obiekty z niestandardową przeglądarką właściwości.

Modyfikacje dostarczone przez wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> zastosowane do implementacji elementu pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> mogą mieć jeden z dwóch zakresów:

- Global--dla wszystkich nowych wystąpień danego składnika

- Lokalne — dotyczy tylko wystąpienia składnika utworzonego na powierzchni projektowej udostępnionej przez bieżącą pakietu VSPackage.

`IsGlobal`Właściwość <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> wystąpienia zastosowana do implementacji elementu pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> określa ten zakres.

Zastosowanie atrybutu do implementacji <xref:Microsoft.VisualStudio.Shell.Package> z <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> właściwością <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> obiektu ustawionego na `true` , jak poniżej, zmienia przeglądarkę dla całego środowiska programu Visual Studio:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Jeśli Flaga globalna została ustawiona na `false` , wówczas zmiana metadanych jest lokalna dla bieżącego projektanta obsługiwanego przez bieżącą pakietu VSPackage:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> Powierzchnia projektowa obsługuje tylko Tworzenie składników, a w związku z tym tylko składniki mogą mieć lokalne metadane. W powyższym przykładzie podjęto próbę zmodyfikowania właściwości, takiej jak `Color` właściwość obiektu. Jeśli `false` została przeniesiona do flagi globalnej, `CustomBrowser` nigdy nie zostanie wyświetlona, ponieważ Projektant nigdy nie tworzy wystąpienia `Color` . Ustawienie flagi globalnej na `false` jest przydatne w przypadku składników, takich jak kontrolki, czasomierze i okna dialogowe.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Zwiększ obsługę czasu projektowania](/previous-versions/37899azc(v=vs.140))