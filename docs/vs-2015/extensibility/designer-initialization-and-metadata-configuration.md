---
title: Inicjowanie projektanta i konfiguracja metadanych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK], initializing
- designers [Visual Studio SDK], configuring metadata
ms.assetid: f7fe9a7e-f669-4642-ad5d-186b2e6e6ec9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2dec3937616c712c56b7012949e044702e6b11f2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703071"
---
# <a name="designer-initialization-and-metadata-configuration"></a>Inicjowanie projektanta i konfiguracja metadanych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Manipulowanie atrybutów metadanych i filtrów skojarzonych z projektanta lub składnika projektanta udostępnia mechanizm dla aplikacji w celu zdefiniowania, jakie narzędzia są używane przez konkretnego projektanta do obsługi różnych <xref:System.Type> obiektów (takich jak struktury danych klasy lub graficznego podmioty), gdy projektant jest dostępna i jak Visual Studio IDE jest skonfigurowany do obsługi projektanta (dla wystąpienia, które **przybornika** kategorii lub karta jest dostępna).  
  
 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] Zapewnia kilka metod w celu ułatwienia kontroli inicjowania projektanta lub składnika projektanta i manipulowania ich metadanych przez pakietu VSPackage.  
  
## <a name="initializing-metadata-and-configuration-information"></a>Inicjowanie metadanych i informacje o konfiguracji  
 Ponieważ są one załadowane na żądanie, pakietów VSPackage nie mógł zostać załadowany przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowisku przed wystąpienia projektanta. W związku z tym, pakietów VSPackage nie można użyć standardowego mechanizmu do konfigurowania projektanta lub składnika projektanta przy tworzeniu, która umożliwia obsługę <xref:System.ComponentModel.Design.IDesignerEventService.DesignerCreated> zdarzeń. Zamiast tego pakietu VSPackage implementuje wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> interfejs i rejestruje się w celu zapewnienia dostosowania, nazywane rozszerzeniami powierzchni projektowania.  
  
### <a name="customizing-initialization"></a>Dostosowywanie inicjowania  
 Dostosowywanie projektanta, składnika lub powierzchni projektanta, obejmuje:  
  
1. Modyfikowanie metadane projektanta i efektywnie zmieniając jak określony <xref:System.Type> jest dostępny lub przekonwertować.  
  
     Jest to zazwyczaj wykonywane za pośrednictwem <xref:System.Drawing.Design.UITypeEditor> lub <xref:System.ComponentModel.TypeConverter> mechanizmów.  
  
     Na przykład, gdy <xref:System.Windows.Forms>— są inicjowane na podstawie projektantów, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] modyfikuje środowiska <xref:System.Drawing.Design.UITypeEditor> dla <xref:System.Web.UI.WebControls.Image> obiekty używane przy użyciu projektanta do używania usługi resource manager w celu uzyskania, mapy bitowe, a nie w systemie plików.  
  
2. Integracja ze środowiskiem, na przykład przez subskrybowanie zdarzeń i uzyskiwanie informacji o konfiguracji projektu. Możesz uzyskać informacje o konfiguracji projektu i subskrybowanie zdarzeń, uzyskując <xref:System.ComponentModel.Design.ITypeResolutionService> interfejsu.  
  
3. Modyfikowanie środowiska użytkownika, aktywując odpowiednie **przybornika** kategorii lub przez ograniczenie możliwości zastosowania projektanta, stosując wystąpienie <xref:System.ComponentModel.ToolboxItemFilterAttribute> klasy do projektanta.  
  
### <a name="designer-initialization-by-a-vspackage"></a>Inicjowanie projektanta przez pakietu VSPackage  
 Pakietu VSPackage powinna obsługiwać Inicjowanie projektanta przez:  
  
1. Tworzenie, wdrażanie obiektu <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> klasy.  
  
   > [!NOTE]
   > <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> Klasy nigdy nie powinny zostać wdrożone na tym samym obiekcie jako <xref:Microsoft.VisualStudio.Shell.Package> klasy.  
  
2. Rejestrowanie klasy wykonania <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> jako świadczenie pomocy technicznej dla projektanta rozszerzenia pakietu VSPackage, stosując wystąpień <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>, <xref:Microsoft.VisualStudio.Shell.ProvideObjectAttribute> i <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> do klasy, zapewniając wdrożenia pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> .  
  
   Po każdym utworzeniu wszelkie projektanta lub składnika projektanta [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowiska:  
  
3. Uzyskuje dostęp do każdego dostawcy rozszerzenia powierzchni projektowania zarejestrowane.  
  
4. Tworzy i inicjuje wystąpienie każdego dostawcy rozszerzenia powierzchni projektowania <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiektu  
  
5. Wywołuje każdego dostawcy rozszerzenia powierzchni projektowania <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnDesignerCreated%2A> metody lub <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension.OnComponentCreated%2A> — metoda (odpowiednio).  
  
   Podczas implementowania <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiekt będący członkiem pakietu VSPackage, jest ważne zrozumieć, że:  
  
6. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Środowiska nie zapewnia żadnych kontrolę nad jakie metadane lub ustawienia konfiguracji, w szczególności `DesignSurfaceExtension` modyfikuje dostawcy. Jest możliwe dla co najmniej dwóch `DesignSurfaceExtension` modyfikowanie tej samej funkcji projektanta powodujące konflikt sposoby, za pomocą końcowych modyfikacji jest ostateczne dostawców. Jest nieokreślony modyfikacji, które jest ostatnio zastosowane.  
  
7. Można jawnie ograniczyć implementację <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension> obiektu określonego projektantów, stosując wystąpień <xref:System.ComponentModel.ToolboxItemFilterAttribute> tej implementacji. Aby uzyskać więcej informacji na temat **przybornika** elementu filtrowania, zobacz <xref:System.ComponentModel.ToolboxItemFilterAttribute> i <xref:System.ComponentModel.ToolboxItemFilterType>.  
  
## <a name="additional-metadata-provisioning"></a>Inicjowanie obsługi administracyjnej dodatkowych metadanych  
 Pakietu VSPackage można zmienić konfigurację projektanta lub składnika projektanta innych niż w czasie projektowania.  
  
 <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> Klasy można programowo, lub można zastosować do VSPackage, zapewniając projektanta.  
  
 Wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> klasa jest używana do zmodyfikowania metadanych składniki rozwiązań utworzone na powierzchni projektowej. Na przykład jeden zastąpić domyślną przeglądarkę właściwości używane przez <xref:System.Windows.Forms.CommonDialog> obiektów za pomocą przeglądarki właściwości niestandardowej.  
  
 Modyfikacje, dostarczone przez wystąpienie <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> stosowane do wdrożenia pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> może mieć jedną z dwóch zakresów:  
  
- Global — dla wszystkich nowych wystąpień danego składnika  
  
- Lokalne — dotyczy tylko wystąpienia składnika, który został utworzony na powierzchni projektowej dostarczane przez bieżącego pakietu VSPackage.  
  
  `IsGlobal` Właściwość <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> wystąpienia stosowane do wdrożenia pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package> określa ten zakres.  
  
  Stosowanie atrybutu do implementacji <xref:Microsoft.VisualStudio.Shell.Package> z <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute.IsGlobal%2A> właściwość <xref:Microsoft.VisualStudio.Shell.Design.ProvideDesignerMetadataAttribute> wartość obiektu `true`, zmienia się poniżej, przeglądarka dla całego [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowiska:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=true`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
  Jeśli ustawiono flagę globalną `false`, a następnie zmiany metadanych jest lokalny biezacym projektantem obsługiwany przez bieżącego pakietu VSPackage:  
  
  `[ProvideDesignerMetadata(typeof(Color), typeof(CustomBrowser),`   `IsGlobal=false`  `)]`  
  
  `internal class MyPackage : Package {}`  
  
> [!NOTE]
> W chwili obecnej powierzchni projektowej obsługuje tylko tworzenie składników, a więc metadanymi lokalnymi tylko te elementy. W powyższym przykładzie mamy próba modyfikowanie właściwości, takie jak `Color` właściwości obiektu. Jeśli `false` została przekazana dla flagę globalną `CustomBrowser` nigdy nie zostanie wyświetlony, ponieważ projektant nigdy tworzone jest wystąpienie `Color`. Ustawienie flagi globalne `false` przydaje się do składników, takich jak formanty, czasomierze i oknach dialogowych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtension>   
 <xref:Microsoft.VisualStudio.Shell.Design.DesignSurfaceExtensionAttribute>   
 <xref:System.ComponentModel.ToolboxItemFilterType>   
 [Rozszerzenie obsługi w czasie projektowania](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
