---
title: Inicjowanie projektanta i konfiguracja metadanych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ed1852780e8045f298ed30f10ace5d971776294
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60075873"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Projektanta konfiguracji inicjowania i metadane

Manipulowanie atrybutów metadanych i filtrów skojarzonych z projektanta lub składnika projektanta udostępnia mechanizm dla aplikacji w celu zdefiniowania, jakie narzędzia są używane przez konkretnego projektanta do obsługi różnych <xref:System.Type> obiektów (takich jak struktury danych klasy lub graficznego podmioty), gdy projektant jest dostępna i jak Visual Studio IDE jest skonfigurowany do obsługi projektanta (dla wystąpienia, które **przybornika** kategorii lub karta jest dostępna).

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Zapewnia kilka metod w celu ułatwienia kontroli inicjowania projektanta lub składnika projektanta i manipulowania ich metadanych przez pakietu VSPackage.

## <a name="initialize-metadata-and-configuration-information"></a>Inicjowanie metadanych i informacje dotyczące konfiguracji
 Ponieważ są one załadowane na żądanie, pakietów VSPackage mogły nie zostać załadowane przez środowisko Visual Studio przed wystąpienia projektanta. W związku z tym, pakietów VSPackage nie można użyć standardowego mechanizmu do konfigurowania projektanta lub składnika projektanta przy tworzeniu, która umożliwia obsługę <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> zdarzeń. Zamiast tego pakietu VSPackage implementuje wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> interfejs i rejestruje się w celu zapewnienia dostosowania, nazywane rozszerzeniami powierzchni projektowania.

### <a name="customize-initialization"></a>Dostosowywanie inicjowania

Dostosowywanie projektanta, składnika lub powierzchni projektanta, obejmuje:

1. Modyfikowanie metadane projektanta i efektywnie zmieniając jak określony <xref:System.Type> jest dostępny lub przekonwertować.

    Jest to zazwyczaj wykonywane za pośrednictwem <xref:System.Drawing.Design.UITypeEditor> lub <xref:System.ComponentModel.TypeConverter> mechanizmów.

    Na przykład, gdy <xref:System.Windows.Forms>— są inicjowane na podstawie projektantów, środowiska Visual Studio modyfikuje <xref:System.Drawing.Design.UITypeEditor> dla <xref:System.Web.UI.WebControls.Image> obiekty używane przy użyciu projektanta do używania usługi resource manager w celu uzyskania, mapy bitowe, a nie w systemie plików.

2. Integracja ze środowiskiem, na przykład przez subskrybowanie zdarzeń i uzyskiwanie informacji o konfiguracji projektu. Możesz uzyskać informacje o konfiguracji projektu i subskrybowanie zdarzeń, uzyskując <xref:System.ComponentModel.Design.ITypeResolutionService> interfejsu.

3. Modyfikowanie środowiska użytkownika, aktywując odpowiednie **przybornika** kategorii lub przez ograniczenie możliwości zastosowania projektanta, stosując wystąpienie <xref:System.ComponentModel.ToolboxItemFilterAttribute> klasy do projektanta.

### <a name="designer-initialization-by-a-vspackage"></a>Inicjowanie projektanta przez pakietu VSPackage

Pakietu VSPackage powinna obsługiwać Inicjowanie projektanta przez:

1. Tworzenie, wdrażanie obiektu <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> klasy.

   > [!NOTE]
   > <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Klasy nigdy nie powinny zostać wdrożone na tym samym obiekcie jako <xref:Microsoft.VisualStudio.Shell.Package> klasy.

2. Rejestrowanie klasy, która implementuje <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> jako świadczenie pomocy technicznej dla projektanta rozszerzeń VSPackage. Rejestrowanie klasy, stosując wystąpień <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute>, i <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do klasy, która dostarcza implementację VSPackage <xref:Microsoft.VisualStudio.Shell.Package>.

Zawsze, gdy projektant lub składnika projektanta jest tworzone, środowiska Visual Studio:

- Uzyskuje dostęp do każdego dostawcy rozszerzenia powierzchni projektowania zarejestrowane.

- Tworzy i inicjuje wystąpienie każdego dostawcy rozszerzenia powierzchni projektowania <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiektu.

- Wywołuje każdego dostawcy rozszerzenia powierzchni projektowania <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> metody lub <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> — metoda (odpowiednio).

Podczas implementowania <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiekt będący członkiem pakietu VSPackage, jest ważne zrozumieć, że:

- W środowisku Visual Studio nie zapewnia żadnych kontrolę nad jakie metadane lub ustawienia konfiguracji, w szczególności `DesignSurfaceExtension` modyfikuje dostawcy. Jest możliwe dla co najmniej dwóch `DesignSurfaceExtension` modyfikowanie tej samej funkcji projektanta powodujące konflikt sposoby, za pomocą końcowych modyfikacji jest ostateczne dostawców. Jest nieokreślony modyfikacji, które jest ostatnio zastosowane.

- Można jawnie ograniczyć implementację <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiektu określonego projektantów, stosując wystąpień <xref:System.ComponentModel.ToolboxItemFilterAttribute> tej implementacji. Aby uzyskać więcej informacji na temat **przybornika** elementu filtrowania, zobacz <xref:System.ComponentModel.ToolboxItemFilterAttribute> i <xref:System.ComponentModel.ToolboxItemFilterType>.

## <a name="additional-metadata-provisioning"></a>Inicjowanie obsługi administracyjnej dodatkowych metadanych

Pakietu VSPackage można zmienić konfigurację projektanta lub składnika projektanta innych niż w czasie projektowania.

<xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Klasy, które mogą być używane programowo lub zastosowane do pakietu VSPackage, który zawiera projektanta.

Wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> klasa jest używana do zmodyfikowania metadanych składniki rozwiązań utworzone na powierzchni projektowej. Na przykład jeden zastąpić domyślną przeglądarkę właściwości używane przez <xref:System.Windows.Forms.CommonDialog> obiektów za pomocą przeglądarki właściwości niestandardowej.

Modyfikacje, dostarczone przez wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> stosowane do wdrożenia pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> może mieć jedną z dwóch zakresów:

- Global — dla wszystkich nowych wystąpień danego składnika

- Lokalne — dotyczy tylko wystąpienia składnika, który został utworzony na powierzchni projektowej dostarczane przez bieżącego pakietu VSPackage.

`IsGlobal` Właściwość <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> wystąpienia stosowane do wdrożenia pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> określa ten zakres.

Stosowanie atrybutu do implementacji <xref:Microsoft.VisualStudio.Shell.Package> z <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> właściwość <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> obiektu równa `true`, zmienia się poniżej, przeglądarka dla całego środowiska programu Visual Studio:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`

`internal class MyPackage : Package {}`

Jeśli ustawiono flagę globalną `false`, a następnie zmiany metadanych jest lokalny biezacym projektantem obsługiwany przez bieżącego pakietu VSPackage:

`[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`

`internal class MyPackage : Package {}`

> [!NOTE]
> Powierzchni projektowej obsługuje tylko tworzenie składników, a więc metadanymi lokalnymi tylko te elementy. W powyższym przykładzie mamy próba modyfikowanie właściwości, takie jak `Color` właściwości obiektu. Jeśli `false` została przekazana dla flagę globalną `CustomBrowser` nigdy nie zostanie wyświetlony, ponieważ projektant nigdy tworzone jest wystąpienie `Color`. Ustawienie flagi globalne `false` przydaje się do składników, takich jak formanty, czasomierze i oknach dialogowych.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>
- <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>
- <xref:System.ComponentModel.ToolboxItemFilterType>
- [Rozszerzenie obsługi w czasie projektowania](https://msdn.microsoft.com/Library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)