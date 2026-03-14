# Gokturk-Crypto-Architecture-yoki-Linguistic-Steganography-Engine.
multi-layered cryptographic pipeline using ancient scripts for network evasion
import random

# === 1. LINGVISTIK BAZA (Lug'atlar) ===
# Alifbo, Emoji va Iyerogliflar zanjiri
ALPHABET = "abcdefghijklmnopqrstuvwxyz "
# Emojilar qatlami (Smile tili)
EMOJIS = ["🤐","😎","👽","👻","🤖","👺","💀","👾","🎃","😺","😸","😹","😻","😼","😽","🙀","😿","😾","🙈","🙉","🙊","🐵","🐒","🦍","🦧","🐶","⬛"]
# GökTürk va Misr Iyerogliflari qatlami
GOKTURK = ["𐰀","𐰉","𐰨","𐰑","𐰂","𓆑","𐰍","𓉔","𐰃","𓆓","𐰚","𐰠","𐰢","𐰤","𐰆","𐰯","𐰴","𐰼","𐰽","𐱅","𐰇","𓆑","𓅱","𐰗","𐰖","𐰔","𓄿"]

# === 2. SHIFRLASH ZANJIRI (ENCRYPTION PIPELINE) ===

def generate_honeypot(length=15):
    """Xakerni chalg'itish uchun soxta (axlat) iyerogliflar qatlamini yaratadi."""
    return "".join(random.choice(GOKTURK) for _ in range(length))

def encrypt_full_pipeline(text):
    text = text.lower()
    encoded_core = ""
    
    # 1-QADAM: Matnni Smile (Emoji) tiliga, keyin Iyerogliflarga o'tkazish
    for char in text:
        if char in ALPHABET:
            index = ALPHABET.index(char)
            # Aslida bu yerda Antonim yoki Mo'g'ul tili mantiqini ham qo'shish mumkin
            # Hozircha to'g'ridan-to'g'ri Emoji -> Iyeroglif zanjiri ishlaydi
            encoded_core += GOKTURK[index] 
        else:
            encoded_core += char
            
    # 2-QADAM: Markaziy kodni teskari o'girish (O'ngdan chapga)
    reversed_core = encoded_core[::-1]
    
    # 3-QADAM: Honeypot (Qopqon) qatlamini qo'shish
    # Xabar boshiga va oxiriga soxta kodlar qo'shamiz. 
    # Tizim asl xabarni topishi uchun maxsus belgi (masalan '𓏢') ishlatamiz.
    fake_layer_start = generate_honeypot(random.randint(10, 20))
    fake_layer_end = generate_honeypot(random.randint(10, 20))
    
    separator = "𓏢" # Asosiy qatlamni ajratib turuvchi sirli belgi
    
    final_payload = fake_layer_start + separator + reversed_core + separator + fake_layer_end
    return final_payload

# === 3. DEKODLASH ZANJIRI (DECRYPTION PIPELINE) ===

def decrypt_full_pipeline(payload):
    separator = "𓏢"
    
    # 1-QADAM: Qopqon (Honeypot) qatlamlarini olib tashlash va markazni topish
    try:
        # Xaker buni bilmaydi, u butun matnni tarjima qilishga urinadi
        core_encrypted = payload.split(separator)[1]
    except IndexError:
        return "XATOLIK: Tizim buzilgan yoki axlat kod!"
        
    # 2-QADAM: Matnni to'g'ri holatga (Chapdan o'ngga) qaytarish
    core_straight = core_encrypted[::-1]
    
    # 3-QADAM: Iyerogliflarni qayta harflarga aylantirish
    decrypted_text = ""
    for char in core_straight:
        if char in GOKTURK:
            index = GOKTURK.index(char)
            decrypted_text += ALPHABET[index]
        else:
            decrypted_text += char
            
    return decrypted_text

# === TIZIMNI ISHLATIB KO'RAMIZ ===
if __name__ == "__main__":
    print("🛡️ MTD VA HONEYPOT TIZIMI ISHGA TUSHDI 🛡️\n")
    
    # Foydalanuvchi ma'lumot kiritadi
    xabar = "salom bu maxfiy xabar"
    print(f"[📤 Yuboruvchi kiritdi]: {xabar}\n")
    
    # Ma'lumot tarmoqqa chiqishdan oldin shifrlanadi
    kiber_paket = encrypt_full_pipeline(xabar)
    
    print("==================================================")
    print("🚨 KIBER-HUJUMCHI (Skaner) KO'RAYOTGAN MANZARA 🚨")
    print("Tarmoqdan quyidagi kutilmagan iyerogliflar o'tmoqda:")
    print(kiber_paket)
    print("==================================================\n")
    
    # Qabul qiluvchi tomonda xabar yechiladi
    qabul_qilingan = decrypt_full_pipeline(kiber_paket)
    print(f"[📥 Qabul qiluvchi o'qidi]: {qabul_qilingan}")
