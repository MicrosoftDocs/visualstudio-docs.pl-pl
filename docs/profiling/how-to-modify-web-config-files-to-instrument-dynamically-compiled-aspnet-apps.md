---
title: 'Instrukcje: Modyfikowanie plików Web.Config do Instrumentowania i profilowania dynamicznie skompilowanych aplikacji sieci Web ASP.NET | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 2c3fe6e9efdf787df351ffc41e7d31b76a2162b8
ms.sourcegitcommit: 34840a954ed3446c789e80ee87da6cbf1203cbb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/18/2018
ms.locfileid: "53592628"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Instrukcje: Modyfikowanie plików web.config w celu instrumentowania i profilowania dynamicznie skompilowanych aplikacji sieci web ASP.NET
Możesz użyć [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] metody Instrumentacji narzędzi profilowania do zbierania danych o chronometrażu, dane alokacji pamięci .NET i danych o okresie istnienia obiektu platformy .NET z dynamicznie kompilowany [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web.  

 W tym temacie opisano sposób modyfikowania *web.config* plik konfiguracji, aby włączyć Instrumentację oraz profilowanie [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web.  

> [!NOTE]
>  Nie należy modyfikować *web.config* plików w przypadku użycia metoda profilowania próbkowanie, lub gdy chcesz Instrumentacji wstępnie skompilowanych [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] modułu.  

 Katalog główny *web.config* plik jest **konfiguracji** elementu. Celu instrumentowania i profilowania dynamicznie skompilowanych [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacja internetowa, należy dodać lub zmodyfikować następujące elementy:  

- A **Konfiguracja/środowiska uruchomieniowego/assemblyBinding/dependentAssembly** element, który identyfikuje zestaw Microsoft.VisualStudio.Enterprise.ASPNetHelper, który kontroluje profilowania. **DependentAssembly** element zawiera dwa elementy podrzędne: **assemblyIdentity** i **codeBase**.  

- A **configuration/system.web/compilation** element, który identyfikuje kroku kompilacji po przetwarzaniu profiler dla zestawu docelowego.  

- Dwa **Dodaj** elementy, które określają lokalizację narzędzi Profilujących są dodawane do **Konfiguracja/appSettings** sekcji.  

  Zaleca się utworzenie kopii oryginalnej *web.config* pliku, który można użyć, aby przywrócić konfigurację aplikacji.  

### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>Aby dodać zestaw ASPNetHelper jako element konfiguracji/środowiska uruchomieniowego/assemblyBinding/dependentAssembly  

1. W razie potrzeby dodaj **środowiska uruchomieniowego** element jako element podrzędny **konfiguracji** element; w przeciwnym razie przejdź do następnego kroku.  

    **Środowiska uruchomieniowego** element nie ma żadnych atrybutów. **Konfiguracji** element może mieć tylko jeden **środowiska uruchomieniowego** elementu podrzędnego.  

2. W razie potrzeby dodaj **assemblyBinding** element jako element podrzędny **środowiska uruchomieniowego** element; w przeciwnym razie przejdź do następnego kroku.  

    **Środowiska uruchomieniowego** element może mieć tylko jeden **assemblyBinding** elementu.  

3. Dodaj następujące nazwy atrybutu i wartość, która **assemblyBinding** elementu:  


   | Nazwa atrybutu | Wartość atrybutu |
   |----------------|--------------------------------------|
   | **xmlns** | **Nazwa urn: schemas-microsoft-com:asm.v1** |


4. Dodaj **dependentAssembly** element jako element podrzędny **assemblyBinding** elementu.  

    **DependentAssembly** element nie ma żadnych atrybutów.  

5. Dodaj **assemblyIdentity** element jako element podrzędny elementu **dependentAssembly** elementu.  

6. Dodaj następujące nazwy atrybutów i wartości do **assemblyIdentity** elementu:  


   | Nazwa atrybutu | Wartość atrybutu |
   |--------------------| - |
   | **Nazwa** | **Microsoft.VisualStudio.Enterprise.ASPNetHelper** |
   | **PublicKeyToken** | **b03f5f7f11d50a3a** |
   | **Kultury** | **Niezależny od** |


7. Dodaj **codeBase** element jako element podrzędny elementu **dependentAssembly** elementu.  

8. Dodaj następujące nazwy atrybutów i wartości do **codeBase** elementu:  

   |Nazwa atrybutu|Wartość atrybutu|  
   |--------------------|---------------------|  
   |**version**|**10.0.0.0**|  
   |**href**|`PathToASPNetHelperDll`|  

    `PathToASPNetHelperDll` jest adres URL pliku Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll. Jeśli [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest zainstalowany w lokalizacji domyślnej **href** . wartość powinna być `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`  

```xml  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
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
```  

### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Aby dodać krok po przetwarzaniu program profilujący do elementu configuration/system.web/compilation  

1.  W razie potrzeby dodaj **system.web** element jako element podrzędny **konfiguracji** element; w przeciwnym razie przejdź do następnego kroku.  

     **System.web** element nie ma żadnych atrybutów. **Konfiguracji** element może mieć tylko jeden **system.web** elementu podrzędnego.  

2.  W razie potrzeby dodaj **kompilacji** element jako element podrzędny **system.web** element; w przeciwnym razie przejdź do następnego kroku.  

     **System.web** element może mieć tylko jeden **kompilacji** elementu podrzędnego.  

3.  Usuń wszystkie istniejące atrybuty z **kompilacji** element i Dodaj następujący atrybut nazwy i wartości:  

    |Nazwa atrybutu|Wartość atrybutu|  
    |--------------------|---------------------|  
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, wersja = 10.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a**|  

```xml  
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

### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Aby dodać ustawienia lokalizacji program profilujący do elementu konfiguracji/appSettings  

1. W razie potrzeby dodaj **appSettings** element jako element podrzędny **konfiguracji** element; w przeciwnym razie przejdź do następnego kroku.  

    **AppSettings** element nie ma żadnych atrybutów. **Konfiguracji** element może mieć tylko jeden **appSettings** elementu podrzędnego.  

2. Dodaj **Dodaj** element jako element podrzędny elementu **appSettings** elementu.  

3. Dodaj następujące nazwy atrybutów i wartości do **Dodaj** elementu:  


   | Nazwa atrybutu | Wartość atrybutu |
   |----------------| - |
   | **Klucz** | **Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation** |
   | **value** | `PerformanceToolsFolder` **\VSInstr.exe** |


4. Dodaj kolejną **Dodaj** element jako element podrzędny elementu **appSettings** elementu.  

5. Dodaj następujący atrybut nazwy i wartości do tego **Dodaj** elementu:  

   |Nazwa atrybutu|Wartość atrybutu|  
   |--------------------|---------------------|  
   |**Klucz**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|  
   |**value**|`PerformanceToolsFolder`|  

    `PerformanceToolsFolder` jest to ścieżka, programu profilującego plików wykonywalnych. Aby uzyskać ścieżkę do narzędzi profilowania, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).


```xml  
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
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"  
        />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
```  

## <a name="example"></a>Przykład  
 Poniżej przedstawiono kompletne *web.config* plik, który umożliwia Instrumentację i profilowania dynamicznie skompilowanych [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web. W tym przykładzie przyjęto założenie, że nie wystąpiły żadne inne ustawienia w pliku przed modyfikacją.  

```xml  
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
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\vsinstr.exe"  
            />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 14.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  

```  

## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Instrumentacja dynamicznie skompilowanej aplikacji ASP.NET i zbieranie szczegółowych danych o chronometrażu](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)   
 [Instrukcje: Instrumentacja dynamicznie skompilowanej aplikacji ASP.NET i zbieranie danych pamięci](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)