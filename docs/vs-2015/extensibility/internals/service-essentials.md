---
title: Podstawowa usługa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 407dda2f203b7be20b19c0e296caa9ce1c95b32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696078"
---
# <a name="service-essentials"></a>Podstawowe informacje o usłudze
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usługa jest umową między dwoma pakietów VSPackage. Jeden pakietu VSPackage udostępnia określony zestaw interfejsów dla innego pakietu VSPackage do użycia. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] to sama kolekcja pakietów VSPackage, która udostępnia usługi innym pakietów VSPackage.  
  
 Można na przykład użyć usługi SVsActivityLog do uzyskania interfejsu IVsActivityLog, którego można użyć do zapisu w dzienniku aktywności. Aby uzyskać więcej informacji, zobacz [How to: Use the Activity Log](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Program udostępnia również niektóre wbudowane usługi, które nie są zarejestrowane. Pakietów VSPackage może zastąpić wbudowane lub inne usługi, dostarczając przesłonięcie usługi. Dla każdej usługi dozwolony jest tylko jedno przesłonięcie usługi.  
  
 Usługi nie mają możliwości odnajdowania. W związku z tym należy znać identyfikator usługi (SID) usługi, która ma zostać zużyta, i należy wiedzieć, które interfejsy zapewnia. Dokumentacja referencyjna usługi zawiera te informacje.  
  
- Pakietów VSPackage świadczący usługi są nazywane dostawcami usług.  
  
- Usługi udostępniane innym pakietów VSPackage są nazywane usługami globalnymi.  
  
- Usługi, które są dostępne tylko dla pakietu VSPackage, które je implementują, lub do dowolnego tworzonego obiektu, są nazywane usługami lokalnymi.  
  
- Usługi, które zastępują wbudowane usługi lub usługi udostępniane przez inne pakiety, są nazywane zastępowaniem usługi.  
  
- Usług lub zastąpień usługi są ładowane na żądanie, czyli dostawca usług jest ładowany, gdy usługa, którą zapewnia, jest wymagana przez inny pakietu VSPackage.  
  
- Aby można było obsługiwać ładowanie na żądanie, dostawca usług rejestruje swoje usługi globalne w usłudze [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Aby uzyskać więcej informacji, zobacz [Rejestrowanie usług](../../misc/registering-services.md).  
  
- Po uzyskaniu usługi należy użyć [polecenia QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (kod niezarządzany) lub rzutowania (kod zarządzany) w celu uzyskania odpowiedniego interfejsu, na przykład:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
- Zarządzany kod odnosi się do usługi według jej typu, natomiast niezarządzany kod odnosi się do usługi za pomocą identyfikatora GUID.  
  
- Podczas [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ładowania pakietu VSPackage przekazuje dostawcę usług do pakietu VSPackage w celu udzielenia pakietu VSPackage dostępu do usług globalnych. Jest to nazywane "lokalizacjami" pakietu VSPackage.  
  
- Pakietów VSPackage mogą być dostawcami usług dla tworzonych przez siebie obiektów. Na przykład formularz może wysłać żądanie dotyczące usługi kolorowej do swojej ramki, co może przekazać żądanie do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- Zarządzane obiekty, które są głęboko zagnieżdżone lub nie znajdują się w ogóle, mogą wywołać <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> bezpośredni dostęp do usług globalnych. Aby uzyskać więcej informacji, zobacz [How to: use GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Lista dostępnych usług](../../extensibility/internals/list-of-available-services.md)   
 [Używanie i świadczenie usług](../../extensibility/using-and-providing-services.md)   
 [Rzutowanie i konwersje typów](https://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Rzutowanie](https://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
