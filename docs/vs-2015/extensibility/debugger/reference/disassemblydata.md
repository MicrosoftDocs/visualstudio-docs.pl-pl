---
title: DisassemblyData | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ea21b4ae9e6e852efcc3625dc3af24478bd88155
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794659"
---
# <a name="disassemblydata"></a>DisassemblyData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

W tym artykule opisano jednej instrukcji dezasemblacji dla zintegrowanego środowiska programistycznego (IDE) do wyświetlenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
typedef struct tagDisassemblyData {   
   DISASSEMBLY_STREAM_FIELDS dwFields;  
   BSTR                      bstrAddress;  
   BSTR                      bstrAddressOffset;  
   BSTR                      bstrCodeBytes;  
   BSTR                      bstrOpcode;  
   BSTR                      bstrOperands;  
   BSTR                      bstrSymbol;  
   UINT64                    uCodeLocationId;  
   TEXT_POSITION             posBeg;  
   TEXT_POSITION             posEnd;  
   BSTR                      bstrDocumentUrl;  
   DWORD                     dwByteOffset;  
   DISASSEMBLY_FLAGS         dwFlags;  
} DisassemblyData;  
```  
  
```csharp  
public struct DisassemblyData {   
   public uint          dwFields;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrCodeBytes;  
   public string        bstrOpcode;  
   public string        bstrOperands;  
   public string        bstrSymbol;  
   public ulong         uCodeLocationId;  
   public TEXT_POSITION posBeg;  
   public TEXT_POSITION posEnd;  
   public string        bstrDocumentUrl;  
   public uint          dwByteOffset;  
   public uint          dwFlags;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `dwFields`  
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) stałą, która określa pola, które są wypełnione.  
  
 `bstrAddress`  
 Adres przesunięcia od niektórych punkt początkowy (zazwyczaj początku funkcji skojarzonej).  
  
 `bstrCodeBytes`  
 Bajty kodu w tej instrukcji.  
  
 `bstrOpcode`  
 Kod operacji w tej instrukcji.  
  
 `bstrOperands`  
 Argumenty operacji dla tej instrukcji.  
  
 `bstrSymbol`  
 Nazwa symbolu ewentualnej skojarzonych z tym adresem (symboli publicznych, etykiety i tak dalej).  
  
 `uCodeLocationId`  
 Identyfikator lokalizacji kodu dla tego wiersza dezasemblowany. Jeśli adres kontekst kodu jednego wiersza jest większa niż adres kontekst kodu innego, identyfikator lokalizacji zdezasemblowany kod pierwszego również będą większe niż identyfikator lokalizacji kodu drugiego.  
  
 `posBeg`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) odnosi się do pozycji w dokumencie, gdzie rozpoczyna się danych dezasemblacji.  
  
 `posEnd`  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) odnosi się do pozycji w dokumencie, gdzie kończy się danych dezasemblacji.  
  
 `bstrDocumentUrl`  
 Dokumenty tekstowe, które mogą być reprezentowane jako nazwy pliku, aby uzyskać `bstrDocumentUrl` wypełniane nazwą pliku, gdzie można znaleźć źródła, przy użyciu formatu `file://file name`.  
  
 Dla dokumentów tekstowych, których nie można przedstawić jako nazwy pliku `bstrDocumentUrl` to unikatowy identyfikator dla dokumentu, a aparat debugowania musi implementować [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md) metody.  
  
 To pole może również zawierać dodatkowe informacje na temat sum kontrolnych. Aby uzyskać szczegółowe informacje, zobacz uwagi.  
  
 `dwByteOffset`  
 Liczba bajtów, jaką instrukcja jest od początku wiersza kodu.  
  
 `dwFlags`  
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) Stała określająca flag, które są aktywne.  
  
## <a name="remarks"></a>Uwagi  
 Każdy `DisassemblyData` struktury w tym artykule opisano jednej instrukcji dezasemblacji. Tablica te struktury jest zwracana z [odczytu](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metody.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktura jest używana tylko w przypadku oparte na tekście dokumentów. Zakres kod źródłowy dla tej instrukcji jest wypełniona tylko pierwszej instrukcji, które są generowane na podstawie instrukcji lub wierszu, na przykład, gdy `dwByteOffset == 0`.  
  
 W przypadku dokumentów, które są inne niż tekstowa kontekstu dokumentu można uzyskać od kodu i `bstrDocumentUrl` pole powinno być wartość null. Jeśli `bstrDocumentUrl` pola jest taka sama jak `bstrDocumentUrl` pola w ciągu poprzednich `DisassemblyData` elementu w tablicy, a następnie ustaw `bstrDocumentUrl` ma wartość null.  
  
 Jeśli `dwFlags` pole ma `DF_DOCUMENT_CHECKSUM` Flaga, a następnie informacji o sumie kontrolnej dodatkowe następuje ciąg wskazywany przez `bstrDocumentUrl` pola. W szczególności po terminator pusty ciąg jest zgodna algorytm sumy kontrolnej, który z kolei następuje wartość 4-bajtowych określającą liczbę bajtów w sumy kontrolnej, i który z kolei następuje bajtów sumy kontrolnej identyfikator GUID. Zobacz przykład w tym temacie dotyczące kodowania i dekodowania tego pola w [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
## <a name="example"></a>Przykład  
 `bstrDocumentUrl` Pole może zawierać dodatkowe informacje o innych niż ciąg, jeśli `DF_DOCUMENT_CHECKSUM` flaga jest ustawiona. Proces tworzenia i odczytywania ten ciąg zakodowany jest prosta w [!INCLUDE[vcprvc](../../../includes/vcprvc-md.md)]. Jednak w [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], jest inny sprawy. Dla tych, którzy wiedzieć, w poniższym przykładzie pokazano jeden ze sposobów tworzenia ciąg zakodowany z [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] i jeden sposób dekodowania ciąg zakodowany w [!INCLUDE[csprcs](../../../includes/csprcs-md.md)].  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
namespace MyNamespace  
    class MyClass  
    {  
        string EncodeData(string documentString,  
                          Guid checksumGuid,  
                          byte[] checksumData)  
        {  
            string returnString = documentString;  
  
            if (checksumGuid == null || checksumData == null)  
            {  
                // Nothing more to do. Just return the string.  
                return returnString;  
            }  
  
            returnString += '\0'; // separating null value  
  
            // Add checksum GUID to string.  
            byte[] guidDataArray  = checksumGuid.ToByteArray();  
            int    guidDataLength = guidDataArray.Length;  
            IntPtr pBuffer        = Marshal.AllocCoTaskMem(guidDataLength);  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, guidDataArray[i]);  
            }  
            // Copy guid data bytes to string as wide characters.  
            // Assumption: sizeof(char) == 2.  
            for (int i = 0; i < guidDataLength; i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum count (a 32-bit value).  
            Int32 checksumCount = checksumData.Length;  
            Marshal.StructureToPtr(checksumCount, pBuffer, true);  
            for (int i = 0; i < sizeof(Int32) / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
  
            // Add checksum data.  
            pBuffer = Marshal.AllocCoTaskMem(checksumCount);  
            for (int i = 0; i < checksumCount; i++)  
            {  
                Marshal.WriteByte(pBuffer, i, checksumData[i]);  
            }  
            for (int i = 0; i < checksumCount / sizeof(char); i++)  
            {  
                returnString += (char)Marshal.ReadInt16(pBuffer, i * sizeof(char));  
            }  
            Marshal.FreeCoTaskMem(pBuffer);  
  
            return returnString;  
        }  
  
        void DecodeData(    string encodedString,  
                        out string documentString,  
                        out Guid   checksumGuid,  
                        out byte[] checksumData)  
       {  
           documentString = String.Empty;  
           checksumGuid = Guid.Empty;  
           checksumData = null;  
  
           IntPtr pBuffer = Marshal.StringToBSTR(encodedString);  
           if (null != pBuffer)  
           {  
               int bufferOffset = 0;  
  
               // Parse string out.  String is assumed to be Unicode.  
               documentString = Marshal.PtrToStringUni(pBuffer);  
               bufferOffset += (documentString.Length + 1) * sizeof(char);  
  
               // Parse Guid out.  
               // Read guid bytes from buffer and store in temporary  
               // buffer that contains only the guid bytes. Then the  
               // Marshal.PtrToStructure() can work properly.  
               byte[] guidDataArray  = checksumGuid.ToByteArray();  
               int    guidDataLength = guidDataArray.Length;  
               IntPtr pGuidBuffer    = Marshal.AllocCoTaskMem(guidDataLength);  
               for (int i = 0; i < guidDataLength; i++)  
               {  
                   Marshal.WriteByte(pGuidBuffer, i,  
                                     Marshal.ReadByte(pBuffer, bufferOffset + i);  
               }  
               bufferOffset += guidDataLength;  
               checksumGuid = (Guid)Marshal.PtrToStructure(pGuidBuffer, typeof(Guid));  
               Marshal.FreeCoTaskMem(pGuidBuffer);  
  
              // Parse out the number of checksum data bytes (always 32-bit value).  
              int dataCount = Marshal.ReadInt32(pBuffer, bufferOffset);  
              bufferOffset += sizeof(Int32);  
  
              // Parse out the checksum data.  
              checksumData = new byte[dataCount];  
              for (int i = 0; i < dataCount; i++)  
              {  
                  checksumData[i] = Marshal.ReadByte(pBuffer, bufferOffset + i);  
              }  
           }  
       }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Struktur i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Odczyt](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)   
 [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
