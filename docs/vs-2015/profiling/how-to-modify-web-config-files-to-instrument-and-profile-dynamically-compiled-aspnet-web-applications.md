---
title: 'Instrukcje: Modyfikowanie plików Web.Config w celu instrumentowania i profilowania dynamicznie skompilowanych aplikacji sieci Web ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d9e4fc4dfdff336b9ddcbd04bd031b48a8acc4dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64792160"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Porady: modyfikowanie plików Web.Config w celu instrumentowania i profilowania dynamicznie skompilowanych aplikacji sieci ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] metody instrumentacji narzędzia profilowania można zbierać szczegółowe dane o chronometrażu, dane przydziału pamięci platformy .NET i dane okresu istnienia obiektu platformy .NET z dynamicznie skompilowanych [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web.  
  
 W tym temacie opisano sposób modyfikowania pliku konfiguracji web.config w celu włączenia Instrumentacji i profilowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web.  
  
> [!NOTE]
> Nie trzeba modyfikować pliku web.config podczas korzystania z metody profilowania próbkowania lub gdy chcesz instrumentację wstępnie skompilowanego [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] modułu.  
  
 Katalog główny pliku web.config jest elementem **konfiguracji** . Aby instrumentować i profilować dynamicznie skompilowaną [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikację sieci Web, należy dodać lub zmodyfikować następujące elementy:  
  
- Element **konfiguracji/środowiska uruchomieniowego/zestawubinding/dependentAssembly** , który identyfikuje zestaw Microsoft. VisualStudio. Enterprise. ASPNetHelper, który kontroluje profilowanie. Element **dependentAssembly** zawiera dwa elementy podrzędne: **assemblyIdentity** i **codebase**.  
  
- Element **Configuration/system. Web/compilation** , który identyfikuje krok kompilacji profilera po procesie dla zestawu docelowego.  
  
- Dwa **Dodaj** elementy, które identyfikują lokalizację narzędzi narzędzia profilowania, są dodawane do sekcji **Konfiguracja/AppSettings** .  
  
  Zalecamy utworzenie kopii oryginalnego pliku web.config, którego można użyć do przywrócenia konfiguracji aplikacji.  
  
### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>Aby dodać zestaw ASPNetHelper jako element konfiguracji/środowiska uruchomieniowego/zestawubinding/dependentAssembly  
  
1. W razie potrzeby Dodaj element **Runtime** jako element podrzędny elementu **konfiguracji** ; w przeciwnym razie przejdź do następnego kroku.  
  
     Element **Runtime** nie ma żadnych atrybutów. Element **konfiguracji** może mieć tylko jeden element podrzędny **środowiska uruchomieniowego** .  
  
2. W razie potrzeby Dodaj element **assemblyBinding** jako element podrzędny elementu **Runtime** ; w przeciwnym razie przejdź do następnego kroku.  
  
     Element **Runtime** może mieć tylko jeden element **assemblyBinding** .  
  
3. Dodaj następującą nazwę i wartość atrybutu do elementu **assemblyBinding** :  
  
    |Nazwa atrybutu|Wartość atrybutu|  
    |--------------------|---------------------|  
    |**'Xmlns**|**urn: schematys-Microsoft-com: ASM. v1**|  
  
4. Dodaj element **dependentAssembly** jako element podrzędny elementu **assemblyBinding** .  
  
     Element **dependentAssembly** nie ma żadnych atrybutów.  
  
5. Dodaj element **assemblyIdentity** jako obiekt podrzędny elementu **dependentAssembly** .  
  
6. Dodaj następujące nazwy atrybutów i wartości do elementu **assemblyIdentity** :  
  
    |Nazwa atrybutu|Wartość atrybutu|  
    |--------------------|---------------------|  
    |**Nazwij**|**Microsoft. VisualStudio. Enterprise. ASPNetHelper**|  
    |**PublicKeyToken**|**b03f5f7f11d50a3a**|  
    |**dziedzinie**|**Zerowy**|  
  
7. Dodaj element z bazą **kodu** jako element podrzędny elementu **dependentAssembly** .  
  
8. Dodaj następujące nazwy atrybutów i wartości do elementu **codebase** :  
  
    |Nazwa atrybutu|Wartość atrybutu|  
    |--------------------|---------------------|  
    |**Wersja**|**10.0.0.0**|  
    |**Tag**|`PathToASPNetHelperDll`|  
  
     `PathToASPNetHelperDll` to adres URL pliku Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll. Jeśli [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] program jest zainstalowany w domyślnej lokalizacji, wartość **href** powinna być `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`  
  
```  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity                         name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"                         culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
```  
  
### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Aby dodać krok po procesie profilera do elementu Configuration/system. Web/compilation  
  
1. W razie potrzeby Dodaj element **System. Web** jako element podrzędny elementu **konfiguracji** ; w przeciwnym razie przejdź do następnego kroku.  
  
     Element **System. Web** nie ma żadnych atrybutów. Element **konfiguracji** może mieć tylko jeden element podrzędny **System. Web** .  
  
2. W razie potrzeby Dodaj element **kompilacja** jako element podrzędny elementu **System. Web** ; w przeciwnym razie przejdź do następnego kroku.  
  
     Element **System. Web** może mieć tylko jeden element podrzędny **kompilacji** .  
  
3. Usuń wszystkie istniejące atrybuty z elementu **compilation** i Dodaj następującą nazwę atrybutu i wartość:  
  
    |Nazwa atrybutu|Wartość atrybutu|  
    |--------------------|---------------------|  
    |**assemblyPostProcessorType**|**Microsoft. VisualStudio. Enterprise. Common. AspPerformanceInstrumenter, Microsoft. VisualStudio. Enterprise. ASPNetHelper, Version = 10.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a**|  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
    <configuration>  
```  
  
### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Aby dodać ustawienia lokalizacji profilera do elementu Configuration/appSettings  
  
1. W razie potrzeby Dodaj element **AppSettings** jako element podrzędny elementu **konfiguracji** ; w przeciwnym razie przejdź do następnego kroku.  
  
     Element **AppSettings** nie ma żadnych atrybutów. Element **konfiguracji** może mieć tylko jeden element podrzędny **AppSettings** .  
  
2. Dodaj element **Add** jako element podrzędny elementu **AppSettings** .  
  
3. Dodaj następujące nazwy atrybutów i wartości do elementu **Add** :  
  
    |Nazwa atrybutu|Wartość atrybutu|  
    |--------------------|---------------------|  
    |**głównych**|**Microsoft. VisualStudio. Enterprise. AspNetHelper. VsInstrLocation**|  
    |**wartościami**|`PerformanceToolsFolder`**\VSInstr.Exe**|  
  
4. Dodaj inny element **Add** jako element podrzędny elementu **AppSettings** .  
  
5. Dodaj następujące nazwy atrybutów i wartości do tego elementu **dodawania** :  
  
    |Nazwa atrybutu|Wartość atrybutu|  
    |--------------------|---------------------|  
    |**głównych**|**Microsoft. VisualStudio. Enterprise. AspNetHelper. VsInstrTools**|  
    |**wartościami**|`PerformanceToolsFolder`|  
  
     `PerformanceToolsFolder` jest ścieżką do plików wykonywalnych profilera. Jeśli program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest zainstalowany w domyślnej lokalizacji, wartość będzie **C:\Program Files\Microsoft Visual Studio 10.0 \ Team Tools\Performance Tools**  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        . . .  
        <system.web>  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
        />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
```  
  
## <a name="example"></a>Przykład  
 Poniżej znajduje się kompletny plik web.config, który umożliwia instrumentację i profilowanie dynamicznie skompilowanych [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web. W tym przykładzie przyjęto założenie, że w pliku nie ma innych ustawień przed modyfikacją.  
  
```  
<?xml version="1.0"?>  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity   
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"  
                        culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral,  
                    PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
            />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Instrumentacja dynamicznie skompilowanej aplikacji ASP.NET i zbieranie szczegółowych danych o chronometrażu](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)   
 [Instrukcje: instrumentacja dynamicznie skompilowanej aplikacji ASP.NET i zbieranie danych pamięci](/visualstudio/profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data?view=vs-2015)
