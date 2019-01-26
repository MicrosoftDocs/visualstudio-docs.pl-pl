---
title: 'Instrukcje: Rozwiązywanie problemów z usługami | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 827c4e4aa1857790e090e34c179bffa4a4f439a1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040362"
---
# <a name="how-to-troubleshoot-services"></a>Instrukcje: Rozwiązywanie problemów z usługami
Istnieje kilka typowych problemów, które mogą wystąpić przy próbie usługi:  
  
- Usługa nie jest zarejestrowana na [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
- Według typu interfejsu, a nie przez typ usługi, wymagane są usługi.  
  
- Pakietu VSPackage żądania usługi nie ma zostały ulokowany.  
  
- Dostawca niewłaściwej usługi jest używany.  
  
  Jeśli żądanej usługi nie można uzyskać, wywołanie <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> zwraca wartość null. Zawsze należy sprawdzić dla wartości null po zażądaniu usługi:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
## <a name="to-troubleshoot-a-service"></a>Rozwiązywania problemów z usługą  
  
1. Sprawdź Rejestr systemu, aby zobaczyć, czy usługa została prawidłowo zarejestrowana. Aby uzyskać więcej informacji, zobacz [jak: Oferuje usługi](../extensibility/how-to-provide-a-service.md).  
  
    Następujące *reg* fragment pliku pokazuje, jak usługa SVsTextManager może zostać zarejestrowana:  
  
   ```  
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
   "Name"="SVsTextManager"  
   ```  
  
    W powyższym przykładzie numer wersji jest wersją [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], takie jak 12.0 lub 14.0, klucz {F5E7E71D-1401-11d1-883B-0000F87579D2} jest identyfikatorem usługi (SID), usługi, SVsTextManager i {wartość domyślną F5E7E720-1401-11d1-883B-0000F87579D2} jest identyfikator GUID pakietu VSPackage, który udostępnia usługę Menedżera tekstu pakietu.  
  
2. Gdy wywołujesz GetService, należy użyć typu usługi i nie jest typem interfejsu. Podczas żądania usługi z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> wyodrębnia identyfikator GUID typu. Usługa nie zostanie znaleziony, jeśli następujące warunki:  
  
   1.  Typ interfejsu jest przekazywany do GetService zamiast typu usługi.  
  
   2.  Nie identyfikatora GUID jawnie jest przypisany do interfejsu. W związku z tym system tworzy domyślny identyfikator GUID dla obiektu, zgodnie z potrzebami.  
  
3. Upewnij się, że pakietu VSPackage żądania usługi zostały zlokalizowane. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] po jego konstruowania i przed wywołaniem wystąpienia usługi witryny pakietu VSPackage <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
    Jeśli masz kod w Konstruktorze pakietu VSPackage, który wymaga usługi, przenieś go do `Initialize` metody.  
  
4. Pamiętaj, że używasz prawidłowego dostawcy.  
  
    Nie wszyscy dostawcy usługi są podobne. Dostawcy usług, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przebiegi do okna narzędzi, który różni się od tego, przekazuje on do pakietu VSPackage. Dostawcy usług okna narzędzia obsługującemu <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, ale nie wie o <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Możesz wywołać <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> można pobrać pakietu VSPackage usługodawcy z poziomu okna narzędzia.  
  
    Jeśli okno narzędzia obsługuje formant użytkownika lub innego kontenera kontrolki, kontener będzie znajdować się przez model składnika Windows i nie ma dostępu do dowolnego [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usług. Możesz wywołać <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> można pobrać pakietu VSPackage usługodawcy z w obrębie kontrolki kontenera.  
  
## <a name="see-also"></a>Zobacz także  
 [Lista dostępnych usług](../extensibility/internals/list-of-available-services.md)   
 [Użyj i świadczenia usług](../extensibility/using-and-providing-services.md)   
 [Podstawowe informacje o usłudze](../extensibility/internals/service-essentials.md)