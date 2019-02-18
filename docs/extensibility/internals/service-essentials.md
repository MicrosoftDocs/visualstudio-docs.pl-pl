---
title: Usługa Essentials | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff3fc897c0b413d6882584671f9cebe1ef73d316
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335314"
---
# <a name="service-essentials"></a>Podstawowe informacje o usłudze
Usługa jest Umowa między dwoma pakietami VSPackage. Jednego pakietu VSPackage udostępnia określony zestaw interfejsów dla innego pakietu VSPackage korzystać. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jest to zbiór pakietów VSPackage, które świadczy usługi do innych pakietów VSPackage.

 Na przykład można użyć usługa SVsActivityLog można uzyskać interfejsu IVsActivityLog, które służy do zapisania do dziennika aktywności. Aby uzyskać więcej informacji, zobacz [jak: Korzystanie z dziennika aktywności](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] są także niektóre wbudowane usługi, które nie zostały zarejestrowane. Pakietów VSPackage można zastąpić wbudowanych lub innych usług, zapewniając zastąpienie usług. Zastąpienie tylko jedna usługa jest dozwolony dla każdej usługi.

 Usługi mają nie możliwości odnajdywania. W związku z tym musisz wiedzieć, identyfikator usługi (SID), usługi, które chcą korzystać i musisz wiedzieć, interfejsy, które zawiera. Dokumentacja usługi zawiera te informacje.

- Pakietów VSPackage, które zapewniają usługi są określane jako dostawcy usług.

- Usługi, które są dostarczane do innych pakietów VSPackage są nazywane usług globalnych.

- Usługi, które są dostępne tylko dla pakietu VSPackage, który implementuje je lub do obiektu, który tworzy, są nazywane usługami lokalnymi.

- Usług, które zastępują wbudowanych usług lub usług świadczonych przez inne pakiety są nazywane zastąpienia usługi.

- Usługi lub zastąpienia usługi, które są ładowane na żądanie, oznacza to, że dostawca usług jest ładowany podczas usługi, którą zapewnia, jest wymagany przez innego pakietu VSPackage.

- Aby zapewnić obsługę ładowania na żądanie, dostawca usług rejestruje jej usług globalnych z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Oferuje usługi](../../extensibility/how-to-provide-a-service.md).

- Po uzyskaniu usługi, użyj [QueryInterface](/cpp/atl/queryinterface) (niezarządzany kod) lub rzutowania (kod zarządzany) można pobrać żądanego interfejsu, na przykład:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- Kod zarządzany odnosi się do usługi przez jej typ, kod niezarządzany, który odnosi się do usługi za pomocą identyfikatora GUID.

- Gdy [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ładuje pakietu VSPackage, przekazuje on usługodawcy do pakietu VSPackage, aby udzielić dostępu pakietu VSPackage do usług globalnych. Jest to określane jako "Lokalizacja" pakietu VSPackage.

- Pakietów VSPackage może być dostawcy usług dla obiektów, które tworzą. Na przykład formularz może wysyłać żądania usługi kolorów do ramki, który może przekazywać żądania do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- Zarządzane obiekty, które głęboko zagnieżdżone lub nie jest ulokowany w ogóle, może wywołać <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> uzyskać bezpośredni dostęp do usług globalnych.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Use GetGlobalService

Czasami może być konieczne uzyskiwanie usługi okno narzędzia lub kontroli kontenera, które nie zostały zlokalizowane; w przeciwnym razie ma zostały umieszczone u dostawcy usług, które nie wie o usługę, którą chcesz. Na przykład można zapisywać w dzienniku aktywności ze znajdujących się pod kontrolą. Aby uzyskać więcej informacji na temat tych i innych scenariuszy, zobacz [jak: Rozwiązywanie problemów z usługami](../../extensibility/how-to-troubleshoot-services.md).

Większość usług Visual Studio można uzyskać przez wywołanie statycznego <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> metody.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> korzysta z pamięci podręcznej usługi jest ulokowany dostawcy, który jest inicjowany dowolnego pakietu VSPackage pochodzące z pakietu po raz pierwszy. Musisz gwarantować, że ten warunek jest spełniony; w przeciwnym razie należy przygotować usługę o wartości null.

Na szczęście <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> działa prawidłowo w większości przypadków.

-   Jeśli pakietu VSPackage udostępnia usługę znanego tylko innego pakietu VSPackage, pakietu VSPackage żądania usługi jest ulokowany przed pakietu VSPackage warunkiem, że usługa jest ładowany.

-   Jeśli okno narzędzia jest tworzony przez pakietu VSPackage, pakietu VSPackage jest ulokowany przed utworzeniem okna narzędzia.

-   Jeśli formant kontenera jest hostowana przez okna narzędzia utworzonego przez pakietu VSPackage, pakietu VSPackage jest ulokowany przed utworzeniem kontenera kontrolki.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Aby uzyskać to usługa firmy znajdujące się w kontenerze okna lub kontroli narzędzi

-   Wstaw ten kod w konstruktorze, okno narzędzia lub kontroli kontenera:

    ```csharp
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```

    ```vb
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```

    Ten kod uzyskuje usługi SVsActivityLog i rzutuje IVsActivityLog interfejs, który może służyć do zapisu w dzienniku aktywności. Aby uzyskać przykład, zobacz [jak: Korzystanie z dziennika aktywności](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Zobacz także

- [Lista dostępnych usług](../../extensibility/internals/list-of-available-services.md)
- [Korzystanie z usług i dostarczanie ich](../../extensibility/using-and-providing-services.md)
- [Rzutowanie i konwersje typów](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Rzutowanie](/cpp/cpp/casting)