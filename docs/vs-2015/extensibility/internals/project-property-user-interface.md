---
title: Interfejs użytkownika właściwości projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties [Visual Studio], user interface
- projects [Visual Studio SDK], properties UI
- project properties UI
ms.assetid: b6aec634-8533-476c-9ebd-36536a2288e2
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31840c40f2a494ffd32f5241e2770938138877e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704096"
---
# <a name="project-property-user-interface"></a>Interfejs użytkownika właściwości projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Podtyp projektu może korzystać z elementów w oknie dialogowym **strony właściwości** projektu, ponieważ są one dostarczane przez projekt podstawowy, ukrywać lub tworzyć formanty tylko do odczytu oraz całe strony jako dostarczone lub dodać strony specyficzne dla podtypów projektu do okna dialogowego **strony właściwości** .  
  
## <a name="extending-the-project-property-dialog-box"></a>Rozszerzanie właściwości projektu — okno dialogowe  
 Podtyp projektu implementuje rozszerzalności automatyzacji i obiekty przeglądania konfiguracji projektu. Te rozszerzalności implementują <xref:EnvDTE.IFilterProperties> interfejs, aby zapewnić, że określone właściwości są ukryte lub tylko do odczytu. Okno dialogowe **strony właściwości** projektu podstawowego, zaimplementowane przez projekt podstawowy, ma wpływ na filtrowanie wykonywane przez rozszerzalności automatyzacji.  
  
 Proces rozszerzania **właściwości projektu** okno dialogowe znajduje się poniżej:  
  
- Projekt podstawowy pobiera rozszerzalności z podtypu projektu przez implementację <xref:EnvDTE80.IInternalExtenderProvider> interfejsu. Obiekty przeglądające, Automatyzacja projektów i konfiguracja projektu projektu podstawowego wszystkie implementują ten interfejs.  
  
- Implementacja <xref:EnvDTE80.IInternalExtenderProvider> dla obiektu przeglądanie projektu i delegat obiektu automatyzacji projektu do <xref:EnvDTE80.IInternalExtenderProvider> implementacji agregatora podtypu projektu (czyli `QueryInterface` dla <xref:EnvDTE80.IInternalExtenderProvider> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiektu projektu).  
  
- Obiekt przeglądarki konfiguracji projektu podstawowego jest również wdrażany <xref:EnvDTE80.IInternalExtenderProvider> bezpośrednio w ramach rozszerzania automatyzacji z obiektu konfiguracji podtypu projektu. Jego implementacja deleguje do <xref:EnvDTE80.IInternalExtenderProvider> interfejsu zaimplementowanego przez agregator podtypów projektu.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetProjectItem%2A>, implementowane przez obiekt przeglądania konfiguracji projektu, zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiekt.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject.GetCfg%2A>, również zaimplementowane przez obiekt przeglądania konfiguracji projektu, zwraca <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg> obiekt.  
  
- Podtyp projektu może ustalić odpowiednie CATID dla różnych rozszerzalnych obiektów projektu podstawowego w czasie wykonywania przez pobranie następujących <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> wartości:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>  
  
  Aby określić CATID dla zakresu projektu, podtyp projektu pobiera powyższe właściwości <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>  z `VSITEMID``typedef` . Podtyp projektu może również chcieć kontrolować, które strony okna dialogowego strony **Właściwości** są wyświetlane dla projektu, zależne od konfiguracji i konfiguracji. Niektóre podtypy projektu mogą wymagać usunięcia wbudowanych stron i dodania określonych podtypów projektu. Aby to umożliwić, projekt zarządzanego klienta wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metodę dla następujących właściwości:  
  
- `VSHPROPID_PropertyPagesCLSIDList` — rozdzielana średnikami lista identyfikatorów CLSID niezależnych od konfiguracji stron właściwości.  
  
- `VSHPROPID_CfgPropertyPagesCLSIDList —` rozdzielana średnikami lista identyfikatorów CLSID stron właściwości zależnych od konfiguracji.  
  
  Ponieważ podtyp projektu agreguje <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> obiekt, może przesłonić definicję tych właściwości, aby określić, które okna dialogowe **strony właściwości** są wyświetlane. Podtyp projektu może pobrać te właściwości z wewnętrznego projektu bazowego, a następnie dodać lub usunąć identyfikatory CLSID stosownie do potrzeb.  
  
  Nowe strony właściwości dodane przez podtyp projektu są przekazywane do obiektu przeglądania konfiguracji projektu z podstawowej implementacji projektu. Ten obiekt przeglądania konfiguracji projektu obsługuje rozszerzalności automatyzacji. Aby uzyskać więcej informacji na temat AutomationExtenders, zobacz [implementowanie i korzystanie z rozszerzeń automatyzacji](https://msdn.microsoft.com/library/0d5c218c-f412-4b28-ab0c-33a611f62356). Strony właściwości zaimplementowane przez wywołanie podtypu projektu <xref:EnvDTE.Project.Extender%2A> w celu pobrania własnego obiektu przeglądania konfiguracji podtypu projektu, który rozszerza obiekt przeglądania konfiguracji projektu podstawowego.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:EnvDTE.IFilterProperties>   
 [Okno dialogowe strony właściwości](https://msdn.microsoft.com/4a3d34ac-ed03-45e8-ae60-a0e1aad300e4)
