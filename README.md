# Crypotography-Project
Unique Coding Function
Allows each letter of the alphabet to be replaced with a unique, randomly paired letter. 



import random
message = input("Enter your message: ")
def no_punctuation(message):
    """Converts an input string into a string containing the unicode code points.
    
    Parameters
    ----------
    message : string
        String contains punctuation marks.
        
    Returns
    -------
    message : string
        String no longer contains punctuation marks.
    """
    punctuations = ['.',',','?','!','@','#','$','%','^','&','*','(',')','-','/',':',';',"'",'"','+','=']
    
    for char in message: 
        
        if char in punctuations: 
            message = message.replace(char, "")
            
    return message


def lower_case(message):
    """Makes the letters in the message all lower case.
    
    Parameters
    ----------
    message : string
        Message with capitalization as entered.
        
    Returns
    -------
    capital_message : string
        String no longer contains capital letters.
    """
        
    for char in message: 
        
        capital_message = message.lower()
        
    return capital_message
    
def reverse(capital_message):
    """Rerverses the string so that the lower case message reads backwards
    
    Parameters
    ----------
    capital_message : string
        String is all lower case.
        
    Returns
    -------
    rev_mess : string
        String now reads backwards.
    """
    
    rev_mess = capital_message[::-1]
    
    return rev_mess


def my_cipher(rev_mess):
    """Encodes message by replacing original letters with different, seemingly randomized letters.
        Uses maketrans() to translate message.
    
    Parameters
    ----------
    rev_mess : string
        String reads backwards, all lower case, no punctuation.
        
    Returns
    -------
    coded_message : string
        Encoded message is finalized. 
    """
        
    alpha_bet = "abcdefghijklmnopqrstuvwxyz0123456789"
    new_alpha = "ijefstzabkpuvwlmnoxyqrcdgh7654098312"
    
    top_secret = rev_mess.maketrans(alpha_bet, new_alpha)
    coded_message=(rev_mess.translate(top_secret))
    
    return(coded_message)
    
    def create_my_code(message):
    
    message = no_punctuation(message)
    message = lower_case(message)
    message = reverse(message)
    message = my_cipher(message)
    
    final_message = my_cipher(message)
    
    return final_message
print(create_my_code(message))

print("Your secret message is ready: ",create_my_code(message) )

#test functions:

def test_no_punctuation():
    
    assert isinstance(no_punctuation('string'),string)
    assert no_punctuation('yes&*#;:?') == 'yes'
    
def test_lower_case():
    
    assert isinstance(lower_case('string'),string)
    assert no_punctuation('CAPITAL LETTERS') == 'capital letters'
    
def test_reverse():
    
    assert isinstance(reverse('string',string))
    assert reverse('abcdefg') == 'gfedcba'

def test_my_cipher(): 
    
    assert isinstance(my_cipher('string'),string)
    assert my_cipher('coding') == 'elfbwz'
