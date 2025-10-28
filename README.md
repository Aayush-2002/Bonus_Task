# Bonus_Task

# views.py:
from rest_framework.response import Response
from rest_framework.views import APIView

class AdultStudentsAPIView(APIView):
    def get(self, request):
        adults = Student.objects.filter(age__gt=18)
        serializer = StudentSerializer(adults, many=True)
        return Response(serializer.data)

# urls.py
path('api/students/adults/', AdultStudentsAPIView.as_view(), name='adult-students'),
