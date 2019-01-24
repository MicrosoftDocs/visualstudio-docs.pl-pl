---
title: Usługa Essentials | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 90b16c9d7e7a762b6c1dac322ae9467b835476fd
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54763991"
---
# <a name="service-essentials"></a>Podstawowe informacje o usłudze
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Usługa jest Umowa między dwoma pakietami VSPackage. Jednego pakietu VSPackage udostępnia określony zestaw interfejsów dla innego pakietu VSPackage korzystać. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] jest to zbiór pakietów VSPackage, które świadczy usługi do innych pakietów VSPackage.  
  
 Na przykład można użyć usługa SVsActivityLog można uzyskać interfejsu IVsActivityLog, które służy do zapisania do dziennika aktywności. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z dziennika aktywności](../../extensibility/how-to-use-the-activity-log.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] są także niektóre wbudowane usługi, które nie zostały zarejestrowane. Pakietów VSPackage można zastąpić wbudowanych lub innych usług, zapewniając zastąpienie usług. Zastąpienie tylko jedna usługa jest dozwolony dla każdej usługi.  
  
 Usługi mają nie możliwości odnajdywania. W związku z tym musisz wiedzieć, identyfikator usługi (SID), usługi, które chcą korzystać i musisz wiedzieć, interfejsy, które zawiera. Dokumentacja usługi zawiera te informacje.  
  
-   Pakietów VSPackage, które zapewniają usługi są określane jako dostawcy usług.  
  
-   Usługi, które są dostarczane do innych pakietów VSPackage są nazywane usług globalnych.  
  
-   Usługi, które są dostępne tylko dla pakietu VSPackage, który implementuje je lub do obiektu, który tworzy, są nazywane usługami lokalnymi.  
  
-   Usług, które zastępują wbudowanych usług lub usług świadczonych przez inne pakiety są nazywane zastąpienia usługi.  
  
-   Usługi lub zastąpienia usługi, które są ładowane na żądanie, oznacza to, że dostawca usług jest ładowany podczas usługi, którą zapewnia, jest wymagany przez innego pakietu VSPackage.  
  
-   Aby zapewnić obsługę ładowania na żądanie, dostawca usług rejestruje jej usług globalnych z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [rejestrowania usług](../../misc/registering-services.md).  
  
-   Po uzyskaniu usługi, użyj [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (niezarządzany kod) lub rzutowania (kod zarządzany) można pobrać żądanego interfejsu, na przykład:  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
-   Kod zarządzany odnosi się do usługi przez jej typ, kod niezarządzany, który odnosi się do usługi za pomocą identyfikatora GUID.  
  
-   Gdy [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ładuje pakietu VSPackage, przekazuje on usługodawcy do pakietu VSPackage, aby udzielić dostępu pakietu VSPackage do usług globalnych. Jest to określane jako "Lokalizacja" pakietu VSPackage.  
  
-   Pakietów VSPackage może być dostawcy usług dla obiektów, które tworzą. Na przykład formularz może wysyłać żądania usługi kolorów do ramki, który może przekazywać żądania do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
-   Zarządzane obiekty, które głęboko zagnieżdżone lub nie jest ulokowany w ogóle, może wywołać <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> uzyskać bezpośredni dostęp do usług globalnych. Aby uzyskać więcej informacji, zobacz [jak: Use GetGlobalService](../../misc/how-to-use-getglobalservice.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Lista dostępnych usług](../../extensibility/internals/list-of-available-services.md)   
 [Korzystanie z usług i dostarczanie](../../extensibility/using-and-providing-services.md)   
 [Rzutowanie i konwersje typów](http://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [Rzutowanie](http://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
