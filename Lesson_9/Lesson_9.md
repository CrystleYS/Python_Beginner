***L9: Building LLM prompts with variables***
In the next cell, you will import the function print_llm_response that uses an LLM with an instruction that you provide as a string and displays the result.

Download helper_function.py
pls set Secrets Variable for Gemini in Collab
GEMINI_API_KEY
Get API KEY From Google AI Studio

!curl -o helper_functions.py https://raw.githubusercontent.com/panaversity/learn-cloud-native-modern-ai-python/main/04_natural_language_programming/02_ai_python_for_beginners/course1_basics/Lesson_9/helper_functions.py
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
100  3944  100  3944    0     0  40276      0 --:--:-- --:--:-- --:--:-- 40659
from helper_functions import print_llm_response
Basically, you can use that function as if you were asking a chatbot. You just need to provide your instructions as a string. For instance, you can ask "What is the capital of France?" using the following code:

print_llm_response("What is the capital of France?")
The capital of France is **Paris**. 

Let's ask the LLM for the lifestyle description for Otto Matic, whose name is stored in name, if he were a dog_age years old dog.

name : str = "Otto Matic"
dog_age : float  = 21/7
print_llm_response(f"""If {name} were a dog, he would be {dog_age} years old.
Describe what life stage that would be for a dog and what that might
entail in terms of energy level, interests, and behavior.""")
If Otto Matic were a dog, being 3.0 years old would put him squarely in his **early adulthood** stage. This is a time of peak physical and mental maturity for most dogs. 

Here's what this might entail:

**Energy Level:** While still energetic, a 3-year-old dog might have slightly calmed down from the boundless energy of a puppy. They'll likely still enjoy long walks and playtime, but might be more content with a shorter nap afterwards. 

**Interests:** This age is often a time of exploration and discovery for dogs. Otto may develop strong interests in particular toys or games, become more interested in exploring his surroundings, or show a new passion for learning tricks. 

**Behavior:**  At 3, Otto would be a confident and independent dog. He's likely well-trained and understands his place in the pack. He might be more relaxed and less prone to destructive chewing or excessive barking.  However, he may also be more prone to testing boundaries and displaying stubbornness. This stage is often referred to as the "teenager" phase for dogs!

**Overall, 3-year-old dogs are often at their best. They are full of life, eager to learn and play, and have a newfound independence. It's a wonderful stage for bonding and enjoying all the joy your furry companion has to offer!** 

You just used AI with your own variables! You used an LLM with instructions that included variables you defined in this notebook.

Congratulations 🎉🎉🎉

Variable names restrictions
The following variable names also have some problems. Try to fix them yourself or use the help from the chatbot.

driver : str = "unicorn"
driver's vehicle : str = "colorful, asymmetric dinosaur car"
favorite planet : str = "Pluto
  File "<ipython-input-6-6ac4904789bd>", line 2
    driver's vehicle = "colorful, asymmetric dinosaur car"
          ^
SyntaxError: unterminated string literal (detected at line 2)
Now, update the next cell with any changes you made in the previous cell.

print_llm_response(f"""Write me a 300 word children's story about a {driver} racing
a {driver's vehicle} for the {favorite planet} champion cup.""")
  File "<ipython-input-8-943a03f55416>", line 2
    a {driver's vehicle} for the {favorite planet} champion cup.""")
                                                                   ^
SyntaxError: f-string: unterminated string
Extra practice
Try the exercises below to practice the concepts from this lesson. Read the comments in each cell with the instructions for each exercise.

Feel free to use the chatbot if you need help.

# Fix this code
1favorite-book : str = "1001 Ways to Wear a Hat"
"2002 Ways to Wear a Scarf" = second_fav_book
print(f"My most favorite book is {1favorite-book}, but I also like {second_fav_book})
  File "<ipython-input-9-f0ea60fa9964>", line 2
    1favorite-book : str = "1001 Ways to Wear a Hat"
    ^
SyntaxError: invalid decimal literal
# Make variables for your favorite game, movie, and food.
# Then use print_llm_response to ask the LLM to recommend you
# a new song to listen to based on your likes.

print_llm_response(f"""

""")
ERROR:tornado.access:500 POST /v1beta/models/gemini-1.5-flash:generateContent?%24alt=json%3Benum-encoding%3Dint (127.0.0.1) 3278.37ms
---------------------------------------------------------------------------
InternalServerError                       Traceback (most recent call last)
<ipython-input-10-0d422ef2d352> in <cell line: 5>()
      3 # a new song to listen to based on your likes.
      4 
----> 5 print_llm_response(f"""
      6 
      7 """)

/content/helper_functions.py in print_llm_response(prompt)
     27     and passes it to OpenAI's GPT3.5 model. The function then prints the response of the model.
     28     """
---> 29     llm_response = get_llm_response(prompt)
     30     print(llm_response)
     31 

/content/helper_functions.py in get_llm_response(prompt)
     39         if not isinstance(prompt, str):
     40             raise ValueError("Input must be a string enclosed in quotes.")
---> 41         completion  : GenerateContentResponse = client.generate_content(prompt)
     42         response = completion.text
     43         return response

/usr/local/lib/python3.10/dist-packages/google/generativeai/generative_models.py in generate_content(self, contents, generation_config, safety_settings, stream, tools, tool_config, request_options)
    329                 return generation_types.GenerateContentResponse.from_iterator(iterator)
    330             else:
--> 331                 response = self._client.generate_content(
    332                     request,
    333                     **request_options,

/usr/local/lib/python3.10/dist-packages/google/ai/generativelanguage_v1beta/services/generative_service/client.py in generate_content(self, request, model, contents, retry, timeout, metadata)
    825 
    826         # Send the request.
--> 827         response = rpc(
    828             request,
    829             retry=retry,

/usr/local/lib/python3.10/dist-packages/google/api_core/gapic_v1/method.py in __call__(self, timeout, retry, compression, *args, **kwargs)
    129             kwargs["compression"] = compression
    130 
--> 131         return wrapped_func(*args, **kwargs)
    132 
    133 

/usr/local/lib/python3.10/dist-packages/google/api_core/retry/retry_unary.py in retry_wrapped_func(*args, **kwargs)
    291                 self._initial, self._maximum, multiplier=self._multiplier
    292             )
--> 293             return retry_target(
    294                 target,
    295                 self._predicate,

/usr/local/lib/python3.10/dist-packages/google/api_core/retry/retry_unary.py in retry_target(target, predicate, sleep_generator, timeout, on_error, exception_factory, **kwargs)
    151         except Exception as exc:
    152             # defer to shared logic for handling errors
--> 153             _retry_error_helper(
    154                 exc,
    155                 deadline,

/usr/local/lib/python3.10/dist-packages/google/api_core/retry/retry_base.py in _retry_error_helper(exc, deadline, next_sleep, error_list, predicate_fn, on_error_fn, exc_factory_fn, original_timeout)
    210             original_timeout,
    211         )
--> 212         raise final_exc from source_exc
    213     if on_error_fn is not None:
    214         on_error_fn(exc)

/usr/local/lib/python3.10/dist-packages/google/api_core/retry/retry_unary.py in retry_target(target, predicate, sleep_generator, timeout, on_error, exception_factory, **kwargs)
    142     for sleep in sleep_generator:
    143         try:
--> 144             result = target()
    145             if inspect.isawaitable(result):
    146                 warnings.warn(_ASYNC_RETRY_WARNING)

/usr/local/lib/python3.10/dist-packages/google/api_core/timeout.py in func_with_timeout(*args, **kwargs)
    118                 kwargs["timeout"] = max(0, self._timeout - time_since_first_attempt)
    119 
--> 120             return func(*args, **kwargs)
    121 
    122         return func_with_timeout

/usr/local/lib/python3.10/dist-packages/google/api_core/grpc_helpers.py in error_remapped_callable(*args, **kwargs)
     74     def error_remapped_callable(*args, **kwargs):
     75         try:
---> 76             return callable_(*args, **kwargs)
     77         except grpc.RpcError as exc:
     78             raise exceptions.from_grpc_error(exc) from exc

/usr/local/lib/python3.10/dist-packages/google/ai/generativelanguage_v1beta/services/generative_service/transports/rest.py in __call__(self, request, retry, timeout, metadata)
    844             # subclass.
    845             if response.status_code >= 400:
--> 846                 raise core_exceptions.from_http_response(response)
    847 
    848             # Return the response

InternalServerError: 500 POST https://generativelanguage.googleapis.com/v1beta/models/gemini-1.5-flash:generateContent?%24alt=json%3Benum-encoding%3Dint: An internal error has occurred. Please retry or report in https://developers.generativeai.google/guide/troubleshooting
