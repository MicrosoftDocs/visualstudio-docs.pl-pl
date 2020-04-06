---
title: DemontażDane | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DisassemblyData
helpviewer_keywords:
- DisassemblyData structure
ms.assetid: 10e70aa7-9381-40d3-bdd1-d2cad78ef16c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9dcf3316ba57bbb25ee171cba7e4edc4923fa270
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737287"
---
# <a name="disassemblydata"></a>DisassemblyData
W tym artykule opisano jedną instrukcję demontażu dla zintegrowanego środowiska programistycznego (IDE) do wyświetlenia.

## <a name="syntax"></a>Składnia

```cpp
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
`dwFields`\
Stała [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md) określająca, które pola są wypełniane.

`bstrAddress`\
Adres jako przesunięcie od pewnego punktu początkowego (zwykle początek skojarzonej funkcji).

`bstrCodeBytes`\
Bajty kodu dla tej instrukcji.

`bstrOpcode`\
Opcode dla tej instrukcji.

`bstrOperands`\
Argumenty do tej instrukcji.

`bstrSymbol`\
Nazwa symbolu, jeśli istnieje, skojarzona z adresem (symbol publiczny, etykieta itd.).

`uCodeLocationId`\
Identyfikator lokalizacji kodu dla tego zdemontowany wiersz. Jeśli adres kontekstu kodu jednego wiersza jest większy niż adres kontekstu kodu innego, a następnie zdemontowany identyfikator lokalizacji kodu pierwszego będzie również większy niż identyfikator lokalizacji kodu drugiego.

`posBeg`\
[TEXT_POSITION,](../../../extensibility/debugger/reference/text-position.md) który odpowiada pozycji w dokumencie, w którym rozpoczyna się demontaż danych.

`posEnd`\
[TEXT_POSITION,](../../../extensibility/debugger/reference/text-position.md) który odpowiada pozycji w dokumencie, w którym kończy się dane demontażu.

`bstrDocumentUrl`\
W przypadku dokumentów tekstowych, które mogą `bstrDocumentUrl` być reprezentowane jako nazwy plików, pole jest wypełniane nazwą pliku, w której można znaleźć źródło, przy użyciu formatu `file://file name`.

W przypadku dokumentów tekstowych, które `bstrDocumentUrl` nie mogą być reprezentowane jako nazwy plików, jest unikatowym identyfikatorem dokumentu, a aparat debugowania musi implementować metodę [GetDocument.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)

To pole może również zawierać dodatkowe informacje o sumach kontrolnych. Zobacz Uwagi, aby uzyskać szczegółowe informacje.

`dwByteOffset`\
Liczba bajtów instrukcji jest od początku wiersza kodu.

`dwFlags`\
Stała [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md) określająca, które flagi są aktywne.

## <a name="remarks"></a>Uwagi
Każda `DisassemblyData` struktura opisuje jedną instrukcję demontażu. Tablica tych struktur jest zwracana z [Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metody.

Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) jest używana tylko dla dokumentów tekstowych. Zakres kodu źródłowego dla tej instrukcji jest wypełniany tylko dla pierwszej instrukcji `dwByteOffset == 0`wygenerowanej z instrukcji lub wiersza, na przykład, gdy .

W przypadku dokumentów, które nie są tekstowe, kontekst dokumentu można `bstrDocumentUrl` uzyskać z kodu, a pole powinno być wartością null. Jeśli `bstrDocumentUrl` pole jest takie `bstrDocumentUrl` samo jak `DisassemblyData` pole w poprzednim `bstrDocumentUrl` elemencie tablicy, należy ustawić wartość null.

Jeśli `dwFlags` pole ma `DF_DOCUMENT_CHECKSUM` ustawioną flagę, dodatkowe informacje o sumie kontrolnej są zgodne z ciągiem wskazywowym `bstrDocumentUrl` przez pole. W szczególności po terminatorze ciągów zerowych następuje identyfikator GUID identyfikujący algorytm sumy kontrolnej, który z kolei następuje 4 bajtów wartość wskazująca liczbę bajtów w sumie kontrolnej i że z kolei następuje suma kontrolna bajtów. Zobacz przykład w tym temacie, jak kodować i [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]dekodować to pole w .

## <a name="example"></a>Przykład
Pole `bstrDocumentUrl` może zawierać dodatkowe informacje inne `DF_DOCUMENT_CHECKSUM` niż ciąg, jeśli flaga jest ustawiona. Proces tworzenia i odczytywania tego zakodowanego [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]ciągu jest prosty w pliku . Jednak w [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)], to inna sprawa. Dla tych, którzy są ciekawi, poniższy przykład pokazuje [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)] jeden sposób, aby utworzyć zakodowany [!INCLUDE[csprcs](../../../data-tools/includes/csprcs_md.md)]ciąg z i jeden sposób, aby zdekodować zakodowany ciąg w .

```csharp
using System;
using System.Runtime.InteropServices;

namespace MyNamespace
{
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
            for (int i = 0; i < guidDataLength / sizeof(char); i++)
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

                // Parse string out. String is assumed to be Unicode.
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
                                      Marshal.ReadByte(pBuffer, bufferOffset + i));
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
- [Struktury i związki](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Odczyt](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
- [DISASSEMBLY_STREAM_FIELDS](../../../extensibility/debugger/reference/disassembly-stream-fields.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
- [DISASSEMBLY_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)
